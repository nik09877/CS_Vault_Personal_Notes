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

