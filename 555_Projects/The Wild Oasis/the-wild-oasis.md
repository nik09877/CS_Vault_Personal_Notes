- Next.js Tailwind Typescript prisma and MongoDB and Zustand
- I could have used MySQL also but I wanted to focus more on availability
- Read about JWT
- There was some hydration error when passing the `created-at / email-verified-at` `Date()` object to client components so I had to serialize / sanitize them and converted them to strings.
- Showed the Map using react-leaflet library using `next/dynamic` inside the `<RentModal/>`Component because leaflet is not supported by react , so had to use this hack.
- 
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