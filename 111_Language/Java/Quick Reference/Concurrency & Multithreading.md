# Threads
- Threads are fundamental units of execution in Java that allow programs to perform multiple tasks concurrently.
- They enable developers to create responsive applications, utilize multi-core processors efficiently and improve overall application performance.

## Process vs Thread
- Process and thread are both fundamental concepts in concurrent computing, but they have distinct characteristics and use cases.

![Process vs Thread](Pasted_image_20250618095617.png)

- Why process doesn't utilize other process threads?
	- Because of a lot of context switching overhead

![](Pasted_image_20250618101132.png)

![[Pasted image 20250618101320.png]]

![[Pasted image 20250618101605.png]]

![[Pasted image 20250618101719.png]]

![[Pasted image 20250618101829.png]]

![[Pasted image 20250618101939.png]]

![[Pasted image 20250618102603.png]]

![[Pasted image 20250618102629.png]]

## Creating Threads in Java

![[Pasted image 20250618103026.png]]

![[Pasted image 20250618103135.png]]

![[Pasted image 20250618103356.png]]

![[Pasted image 20250618103602.png]]

![[Pasted image 20250618103622.png]]

![[Pasted image 20250618103659.png]]

![[Pasted image 20250618103943.png]]

![[Pasted image 20250618104059.png]]

![[Pasted image 20250618104432.png]]

![[Pasted image 20250618104543.png]]

![[Pasted image 20250618104812.png]]

![[Pasted image 20250618104859.png]]

![[Pasted image 20250618104914.png]]

![[Pasted image 20250618104928.png]]

![[Pasted image 20250618105023.png]]

![[Pasted image 20250618105215.png]]

![[Pasted image 20250618105304.png]]

![[Pasted image 20250618105444.png]]

![[Pasted image 20250618105616.png]]

![[Pasted image 20250618105652.png]]

![[Pasted image 20250618105805.png]]

![[Pasted image 20250618105928.png]]

![[Pasted image 20250618110008.png]]

![[Pasted image 20250618110101.png]]

![[Pasted image 20250618110201.png]]

![[Pasted image 20250618110244.png]]

![[Pasted image 20250618110312.png]]

![[Pasted image 20250618110413.png]]

![[Pasted image 20250618110441.png]]

![[Pasted image 20250618110525.png]]

![[Pasted image 20250618110846.png]]

![[Pasted image 20250618111036.png]]

![[Pasted image 20250618111106.png]]

![[Pasted image 20250618112220.png]]

![[Pasted image 20250618112234.png]]

![[Pasted image 20250618112357.png]]

![[Pasted image 20250618112457.png]]

![[Pasted image 20250618112533.png]]

![[Pasted image 20250618112638.png]]

![[Pasted image 20250618112838.png]]

![[Pasted image 20250618112921.png]]

![[Pasted image 20250618113025.png]]

![[Pasted image 20250618113116.png]]

![[Pasted image 20250618113248.png]]

# Thread Pool and Thread lifecycle

![[Pasted image 20250618113529.png]]

![[Pasted image 20250618113602.png]]

![[Pasted image 20250618113752.png]]

![[Pasted image 20250618113848.png]]

![[Pasted image 20250618113930.png]]

![[Pasted image 20250618114028.png]]

![[Pasted image 20250618114106.png]]

![[Pasted image 20250618114156.png]]

![[Pasted image 20250618114211.png]]

![[Pasted image 20250618114255.png]]

![[Pasted image 20250618114315.png]]

![[Pasted image 20250618114429.png]]

![[Pasted image 20250618114440.png]]

![[Pasted image 20250618114526.png]]

![[Pasted image 20250618114555.png]]

![[Pasted image 20250618114617.png]]

![[Pasted image 20250618114842.png]]

![[Pasted image 20250618114857.png]]

![[Pasted image 20250618115118.png]]

![[Pasted image 20250618115328.png]]

![[Pasted image 20250618115444.png]]

![[Pasted image 20250618115528.png]]

![[Pasted image 20250618115612.png]]

![[Pasted image 20250618120024.png]]

![[Pasted image 20250618120121.png]]

![[Pasted image 20250618120140.png]]

![[Pasted image 20250618120240.png]]

![[Pasted image 20250618120304.png]]

- `Execute()` accepts only `Runnable`, but `submit()` accepts `Runnable` and `Callable` and returns a `Future<T>`

![[Pasted image 20250618120630.png]]

![[Pasted image 20250618120648.png]]

![[Pasted image 20250618120747.png]]

![[Pasted image 20250618123418.png]]

![[Pasted image 20250618123908.png]]

![[Pasted image 20250618124140.png]]

![[Pasted image 20250618124449.png]]

![[Pasted image 20250618124504.png]]

![[Pasted image 20250618124621.png]]

![[Pasted image 20250618124733.png]]

![[Pasted image 20250618124829.png]]

![[Pasted image 20250618124945.png]]

![[Pasted image 20250618134038.png]]

![[Pasted image 20250618152542.png]]

![[Pasted image 20250618152624.png]]

![[Pasted image 20250618152800.png]]

![[Pasted image 20250618152925.png]]

![[Pasted image 20250618153522.png]]

![[Pasted image 20250618153643.png]]

![[Pasted image 20250618153738.png]]

![[Pasted image 20250618153804.png]]

![[Pasted image 20250618153816.png]]

![[Pasted image 20250618154250.png]]

![[Pasted image 20250618154305.png]]

# Thread Executors in Java

![[Pasted image 20250618154701.png]]

![[Pasted image 20250618154746.png]]

![[Pasted image 20250618154818.png]]

![[Pasted image 20250618154835.png]]

![[Pasted image 20250618154917.png]]

![[Pasted image 20250618155031.png]]

![[Pasted image 20250618155057.png]]

![[Pasted image 20250618155127.png]]

![[Pasted image 20250618155139.png]]

![[Pasted image 20250618155242.png]]

![[Pasted image 20250618155356.png]]

![[Pasted image 20250618155542.png]]

![[Pasted image 20250618155630.png]]

![[Pasted image 20250618155724.png]]

![[Pasted image 20250618155826.png]]

![[Pasted image 20250618155849.png]]

![[Pasted image 20250618155944.png]]

![[Pasted image 20250618160027.png]]

![[Pasted image 20250618160107.png]]

![[Pasted image 20250618160150.png]]

![[Pasted image 20250618160213.png]]

![[Pasted image 20250618160226.png]]

![[Pasted image 20250618160256.png]]

![[Pasted image 20250618160428.png]]

![[Pasted image 20250618160502.png]]

![[Pasted image 20250618160543.png]]

![[Pasted image 20250618160601.png]]

![[Pasted image 20250618162532.png]]

![[Pasted image 20250618163041.png]]

![[Pasted image 20250618163142.png]]

![[Pasted image 20250618163226.png]]

![[Pasted image 20250618194919.png]]

![[Pasted image 20250618194942.png]]

![[Pasted image 20250618195138.png]]

![[Pasted image 20250618195223.png]]

![[Pasted image 20250618195539.png]]

![[Pasted image 20250618195645.png]]

![[Pasted image 20250618195713.png]]

# Thread Synchronization

![[Pasted image 20250618195846.png]]

![[Pasted image 20250618195906.png]]

![[Pasted image 20250618200208.png]]

![[Pasted image 20250618200551.png]]

![[Pasted image 20250618200626.png]]

![[Pasted image 20250618200917.png]]

![[Pasted image 20250618201023.png]]

![[Pasted image 20250618201249.png]]

![[Pasted image 20250618202111.png]]

![[Pasted image 20250618202209.png]]

![[Pasted image 20250618202441.png]]

![[Pasted image 20250618202546.png]]

![[Pasted image 20250618203341.png]]

- How to avoid bugs like not using `volatile` keyword in Double Checking lock in singleton pattern ?


	1. **Non-volatile Singletons** with double-checked locking.
	    
	2. **Multiple threads accessing a shared variable** without `volatile`/`final`.
	    
	3. **Lazy initialization** without proper synchronization.

![[Pasted image 20250618203912.png]]

![[Pasted image 20250618204027.png]]

![[Pasted image 20250621091701.png]]

![[Pasted image 20250621091926.png]]

![[Pasted image 20250621092054.png]]

![[Pasted image 20250621092108.png]]

# Thread Communication

![[Pasted image 20250621092324.png]]

![[Pasted image 20250621092355.png]]

![[Pasted image 20250621092423.png]]

![[Pasted image 20250621092437.png]]

![[Pasted image 20250621092529.png]]

![[Pasted image 20250621092551.png]]

![[Pasted image 20250621092607.png]]

![[Pasted image 20250621092833.png]]

![[Pasted image 20250621092931.png]]

![[Pasted image 20250621092854.png]]

![[Pasted image 20250621093000.png]]

![[Pasted image 20250621093159.png]]

![[Pasted image 20250621093250.png]]

![[Pasted image 20250621093314.png]]

![[Pasted image 20250621093346.png]]

![[Pasted image 20250621093441.png]]

![[Pasted image 20250621093456.png]]

![[Pasted image 20250621093519.png]]

![[Pasted image 20250621093618.png]]

![[Pasted image 20250621093721.png]]

![[Pasted image 20250621093740.png]]

![[Pasted image 20250621093822.png]]

# Locks and Types of Locks

![[Pasted image 20250621094238.png]]

![[Pasted image 20250621094345.png]]

![[Pasted image 20250621123340.png]]

![[Pasted image 20250621123404.png]]

![[Pasted image 20250621123511.png]]

![[Pasted image 20250621123758.png]]

![[Pasted image 20250621123845.png]]

![[Pasted image 20250621123859.png]]

![[Pasted image 20250621124058.png]]

![[Pasted image 20250621124126.png]]

![[Pasted image 20250621124149.png]]

![[Pasted image 20250621124344.png]]

![[Pasted image 20250621124447.png]]

![[Pasted image 20250621124514.png]]

![[Pasted image 20250621124540.png]]

![[Pasted image 20250621124724.png]]

![[Pasted image 20250621124834.png]]

![[Pasted image 20250621124907.png]]

![[Pasted image 20250621124956.png]]

![[Pasted image 20250621125047.png]]

![[Pasted image 20250621125153.png]]

![[Pasted image 20250621125241.png]]


# Semaphores

![[Pasted image 20250621125650.png]]

![[Pasted image 20250621125751.png]]

![[Pasted image 20250621130523.png]]

![[Pasted image 20250621130626.png]]

![[Pasted image 20250621130645.png]]

![[Pasted image 20250621130752.png]]

![[Pasted image 20250621130808.png]]

![[Pasted image 20250621130913.png]]

![[Pasted image 20250622184032.png]]

![[Pasted image 20250622184159.png]]

![[Pasted image 20250622184219.png]]

![[Pasted image 20250622184343.png]]

![[Pasted image 20250622184403.png]]

![[Pasted image 20250622185634.png]]

![[Pasted image 20250622185719.png]]

![[Pasted image 20250622185833.png]]

![[Pasted image 20250622190423.png]]

![[Pasted image 20250622190556.png]]

![[Pasted image 20250622191029.png]]

![[Pasted image 20250622191353.png]]

![[Pasted image 20250622191414.png]]

![[Pasted image 20250622191435.png]]

![[Pasted image 20250622200608.png]]

![[Pasted image 20250622200638.png]]

![[Pasted image 20250622200651.png]]

![[Pasted image 20250622200706.png]]

![[Pasted image 20250622200733.png]]

# Java Concurrent Collections

![[Pasted image 20250622204442.png]]

![[Pasted image 20250622204513.png]]

![[Pasted image 20250622204529.png]]

![[Pasted image 20250622204628.png]]

![[Pasted image 20250622204716.png]]

![[Pasted image 20250622204726.png]]

![[Pasted image 20250622204738.png]]

![[Pasted image 20250622204753.png]]

![[Pasted image 20250622204945.png]]

![[Pasted image 20250622205010.png]]

![[Pasted image 20250622205143.png]]

![[Pasted image 20250622205206.png]]

![[Pasted image 20250622205407.png]]

![[Pasted image 20250622205420.png]]

![[Pasted image 20250622205451.png]]

![[Pasted image 20250622205535.png]]

![[Pasted image 20250622205554.png]]

![[Pasted image 20250622205624.png]]

![[Pasted image 20250629182627.png]]

![[Pasted image 20250629182707.png]]

![[Pasted image 20250629182755.png]]

![[Pasted image 20250629182847.png]]

![[Pasted image 20250629182857.png]]

![[Pasted image 20250629182931.png]]

![[Pasted image 20250629182945.png]]

![[Pasted image 20250629183253.png]]

![[Pasted image 20250629183353.png]]

![[Pasted image 20250629183431.png]]

![[Pasted image 20250629183521.png]]

![[Pasted image 20250629183802.png]]

