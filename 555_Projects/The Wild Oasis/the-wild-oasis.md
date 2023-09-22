- Next.js Tailwind Typescript prisma and MongoDB and Zustand, image upload using `next-cloudinary`, used `react-date-range` for calendar
- I could have used MySQL also but I wanted to focus more on availability
- Read about JWT
- There was some hydration error when passing the `created-at / email-verified-at` `Date()` object to client components so I had to serialize / sanitize them and converted them to strings.
- Showed the Map using react-leaflet library using `next/dynamic` inside the `<RentModal/>`Component because leaflet is not supported by react , so had to use this hack.
- After doing reservation I am redirecting the user to /trips page, but the data is SSG so it is not getting revalidated
- I had to convert some parts of HomePage to Client Component because of search filters, it should be SSR not SSG in vercel
- Search for rooms in a date range
```javascript
if (startDate && endDate) {
      query.NOT = {
        reservations: {
          some: {
            OR: [
              {
                endDate: { gte: startDate },
                startDate: { lte: startDate },
              },
              {
                startDate: { lte: endDate },
                endDate: { gte: endDate },
              },
            ],
          },
        },
      };
    }
```
- Protected routes :
```javascript
export { default } from 'next-auth/middleware';
export const config = {
  matcher: ['/trips', '/reservations', '/properties', '/favorites'],
};
```
- Dealing with concurrent booking of same room
```javascript
try {
    const listingAndReservation = await prisma.$transaction(async (tx) => {
      //1. find suitable listing
      let query: any = {};
      query.id = listingId;
      query.NOT = {
        reservations: {
          some: {
            OR: [
              {
                endDate: { gte: startDate },
                startDate: { lte: startDate },
              },
              {
                startDate: { lte: endDate },
                endDate: { gte: endDate },
              },
            ],
          },
        },
      };

      const listings = await tx.listing.findMany({
        where: query,
        orderBy: {
          createdAt: 'desc',
        },
      });


      // 2. Verify availability
      const isListingAvailable = listings.some(
        (listing) => listing.id === listingId
      );
      if (!isListingAvailable) {
        throw new Error('Listing Not available');
      }
      // 3. Return reservation
      const listingAndReservation = await tx.listing.update({
        where: {
          id: listingId,
        },
        data: {
          reservations: {
            create: {
              userId: currentUser.id,
              startDate,
              endDate,
              totalPrice,
            },
          },
        },
      });
      return listingAndReservation;
    });
    return NextResponse.json(listingAndReservation);
  } catch (error) {
    return NextResponse.error();
  }
```
# Model

```javascript
model User {
  id              String @id @default(auto()) @map("_id") @db.ObjectId
  name            String?
  email           String?   @unique
  emailVerified   DateTime?
  image           String?
  hashedPassword  String?
  createdAt       DateTime @default(now())
  updatedAt       DateTime @updatedAt
  favoriteIds     String[] @db.ObjectId
  accounts Account[]
  listings Listing[]
  reservations Reservation[]
}

model Account {
  id String @id @default(auto()) @map("_id") @db.ObjectId
  userId             String   @db.ObjectId
  type               String
  provider           String
  providerAccountId  String
  refresh_token      String?  @db.String
  access_token       String?  @db.String
  expires_at         Int?
  token_type         String?
  scope              String?
  id_token           String?  @db.String
  session_state      String?

  user User @relation(fields: [userId], references: [id], onDelete: Cascade)
  @@unique([provider, providerAccountId])
}

model Listing {
  id             String @id @default(auto()) @map("_id") @db.ObjectId
  title String
  description String
  imageSrc String
  createdAt DateTime @default(now())
  category  String
  roomCount Int
  bathroomCount Int
  guestCount Int
  locationValue String
  userId String @db.ObjectId
  price Int
  user User @relation(fields: [userId], references: [id], onDelete: Cascade)
  reservations Reservation[]
}

model Reservation {
  id String @id @default(auto()) @map("_id") @db.ObjectId
  userId String @db.ObjectId
  listingId String @db.ObjectId  
  startDate DateTime
  endDate DateTime
  totalPrice Int
  createdAt DateTime @default(now())
  user User @relation(fields: [userId], references: [id], onDelete: Cascade)
  listing Listing @relation(fields: [listingId], references: [id], onDelete: Cascade)
}
```

# Folder Structure
![](Pasted_image_20230917214433.png)
1. `actions` - contains the fetch functions that retrieve data from the server (`getCurrentUser`, `getAllListings` etc)
2. `api` - contains the `POST`, `DELETE`etc api routes
3. `components` - contains components
4. `hooks` - Acts as Intermediary between the client `pages`/`components` and `actions`/`api`/`state_changes`
5. `libs` - contain the `prismaDB` set up and other library functions/utils
6. `providers` - Third party scripts or services need to be wrapped in a client component, providers are used for this purpose e.g. `<ToasterProvider/>`
7. `types` - Typescript types
8. `prisma` - contains DB Schema