Christy Jacob - CXJ170002

1. For doAnalysis() the provided code is correct. A node d dominates a node n if every path from the entry node to n must go through d, and every node dominates itself. To verify that the code is doAnalysis() is correct, I went step by step through each line of code to find it’s dominators and compared it to the output. The results are at the bottom of the README. The output from the provided doAnalysis() code was correct. 

2. The PTA was more precise than the CHA and took less time. PTA had 7 total edges while CHA had 12 total edges so PTA is more precise since it doesn’t include extra calls that are not true such as animal.saySomething() calling fish.saySomething(). I measured the speed of each in nanoseconds. CHA took 161341400 nanoseconds while PTA took 131600 nanoseconds. Therefore, PTA is faster as well in this case.

3. Here is my output for tracing heap access:
Thread Thread-13 wrote static field <a1.HelloThread: int x>
Thread Thread-14 wrote static field <a1.HelloThread: int x>
Thread Thread-14 read instance field <a1.HelloThread$TestThread: int y> of object Thread[Thread-14,5,Soot Threadgroup]
Thread Thread-14 wrote instance field <a1.HelloThread$TestThread: int y> of object Thread[Thread-14,5,Soot Threadgroup]
Thread Thread-13 read instance field <a1.HelloThread$TestThread: int y> of object Thread[Thread-13,5,Soot Threadgroup]
Thread Thread-13 read static field <a1.HelloThread: int x>
Thread Thread-13 read static field <java.lang.System: java.io.PrintStream out>

Manually Finding Dominators for Question 1
r0 := @this: a1.GCD is dominated by itself

specialinvoke r0.<java.lang.Object: void <init>()>() is dominated by r0 := @this: a1.GCD and itself.

Return is dominated by r0 := @this: a1.GCD, specialinvoke r0.<java.lang.Object: void <init>()>(), and itself

r0 := @parameter0: java.lang.String[] only dominates itself

$i2 = lengthof r0 is dominated by r0 := @parameter0: java.lang.String[] and itself

if $i2 >= 2 goto $r1 = r0[0] is dominated by  r0 := @parameter0: java.lang.String[], $i2 = lengthof r0, and itself

$r11 = <java.lang.System: java.io.PrintStream err> is dominated by if $i2 >= 2 goto $r1 = r0[0], r0 := @parameter0: java.lang.String[], $i2 = lengthof r0, and itself

virtualinvoke $r11.<java.io.PrintStream: void println(java.lang.String)>("java GCD int1 int2\nExample: java GCD 876 267") is dominated by $r11 = <java.lang.System: java.io.PrintStream err>, if $i2 >= 2 goto $r1 = r0[0], r0 := @parameter0: java.lang.String[], $i2 = lengthof r0, and itself

return is dominated by virtualinvoke $r11.<java.io.PrintStream: void println(java.lang.String)>("java GCD int1 int2\nExample: java GCD 876 267"),  $r11 = <java.lang.System: java.io.PrintStream err>, if $i2 >= 2 goto $r1 = r0[0], r0 := @parameter0: java.lang.String[], $i2 = lengthof r0, and itself

$r1 = r0[0] is dominated by if $i2 >= 2 goto $r1 = r0[0], r0 := @parameter0: java.lang.String[], $i2 = lengthof r0, and itself only since the contents inside the if statement don’t necessarily have to run.

i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1) is dominated by $r1 = r0[0], if $i2 >= 2 goto $r1 = r0[0], r0 := @parameter0: java.lang.String[], $i2 = lengthof r0, and itself

$r2 = r0[1] is dominated by i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1),  $r1 = r0[0], if $i2 >= 2 goto $r1 = r0[0], r0 := @parameter0: java.lang.String[], $i2 = lengthof r0, and itself

i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2) is dominated by $r2 = r0[1], i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1),  $r1 = r0[0], if $i2 >= 2 goto $r1 = r0[0], r0 := @parameter0: java.lang.String[], $i2 = lengthof r0, and itself

$r4 = <java.lang.System: java.io.PrintStream out> is dominated by i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2), $r2 = r0[1], i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1),  $r1 = r0[0], if $i2 >= 2 goto $r1 = r0[0], r0 := @parameter0: java.lang.String[], $i2 = lengthof r0, and itself

$r3 = new java.lang.StringBuilder is dominated by $r4 = <java.lang.System: java.io.PrintStream out>, i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2), $r2 = r0[1], i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1),  $r1 = r0[0], if $i2 >= 2 goto $r1 = r0[0], r0 := @parameter0: java.lang.String[], $i2 = lengthof r0, and itself

specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd(") is dominated by $r3 = new java.lang.StringBuilder, $r4 = <java.lang.System: java.io.PrintStream out>, i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2), $r2 = r0[1], i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1),  $r1 = r0[0], if $i2 >= 2 goto $r1 = r0[0], r0 := @parameter0: java.lang.String[], $i2 = lengthof r0, and itself

$r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0) is dominated by specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd("), $r3 = new java.lang.StringBuilder, $r4 = <java.lang.System: java.io.PrintStream out>, i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2), $r2 = r0[1], i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1),  $r1 = r0[0], if $i2 >= 2 goto $r1 = r0[0], r0 := @parameter0: java.lang.String[], $i2 = lengthof r0, and itself

$r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", ") is dominated by $r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0), specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd("), $r3 = new java.lang.StringBuilder, $r4 = <java.lang.System: java.io.PrintStream out>, i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2), $r2 = r0[1], i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1),  $r1 = r0[0], if $i2 >= 2 goto $r1 = r0[0], r0 := @parameter0: java.lang.String[], $i2 = lengthof r0, and itself

$r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1) is dominated by $r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", "), $r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0), specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd("), $r3 = new java.lang.StringBuilder, $r4 = <java.lang.System: java.io.PrintStream out>, i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2), $r2 = r0[1], i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1),  $r1 = r0[0], if $i2 >= 2 goto $r1 = r0[0], r0 := @parameter0: java.lang.String[], $i2 = lengthof r0, and itself

$r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = ") is dominated by $r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1), $r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", "), $r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0), specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd("), $r3 = new java.lang.StringBuilder, $r4 = <java.lang.System: java.io.PrintStream out>, i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2), $r2 = r0[1], i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1),  $r1 = r0[0], if $i2 >= 2 goto $r1 = r0[0], r0 := @parameter0: java.lang.String[], $i2 = lengthof r0, and itself

$i3 = staticinvoke <a1.GCD: int gcd(int,int)>(i0, i1) is dominated by $r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = "), $r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1), $r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", "), $r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0), specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd("), $r3 = new java.lang.StringBuilder, $r4 = <java.lang.System: java.io.PrintStream out>, i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2), $r2 = r0[1], i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1),  $r1 = r0[0], if $i2 >= 2 goto $r1 = r0[0], r0 := @parameter0: java.lang.String[], $i2 = lengthof r0, and itself

$r9 = virtualinvoke $r8.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>($i3) is dominated by $i3 = staticinvoke <a1.GCD: int gcd(int,int)>(i0, i1), $r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = "), $r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1), $r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", "), $r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0), specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd("), $r3 = new java.lang.StringBuilder, $r4 = <java.lang.System: java.io.PrintStream out>, i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2), $r2 = r0[1], i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1),  $r1 = r0[0], if $i2 >= 2 goto $r1 = r0[0], r0 := @parameter0: java.lang.String[], $i2 = lengthof r0, and itself

$r10 = virtualinvoke $r9.<java.lang.StringBuilder: java.lang.String toString()>() is dominated by $r9 = virtualinvoke $r8.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>($i3), $i3 = staticinvoke <a1.GCD: int gcd(int,int)>(i0, i1), $r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = "), $r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1), $r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", "), $r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0), specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd("), $r3 = new java.lang.StringBuilder, $r4 = <java.lang.System: java.io.PrintStream out>, i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2), $r2 = r0[1], i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1),  $r1 = r0[0], if $i2 >= 2 goto $r1 = r0[0], r0 := @parameter0: java.lang.String[], $i2 = lengthof r0, and itself

virtualinvoke $r4.<java.io.PrintStream: void println(java.lang.String)>($r10) is dominated by $r10 = virtualinvoke $r9.<java.lang.StringBuilder: java.lang.String toString()>(), $r9 = virtualinvoke $r8.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>($i3), $i3 = staticinvoke <a1.GCD: int gcd(int,int)>(i0, i1), $r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = "), $r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1), $r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", "), $r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0), specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd("), $r3 = new java.lang.StringBuilder, $r4 = <java.lang.System: java.io.PrintStream out>, i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2), $r2 = r0[1], i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1),  $r1 = r0[0], if $i2 >= 2 goto $r1 = r0[0], r0 := @parameter0: java.lang.String[], $i2 = lengthof r0, and itself

return is dominated by virtualinvoke $r4.<java.io.PrintStream: void println(java.lang.String)>($r10), $r10 = virtualinvoke $r9.<java.lang.StringBuilder: java.lang.String toString()>(), $r9 = virtualinvoke $r8.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>($i3), $i3 = staticinvoke <a1.GCD: int gcd(int,int)>(i0, i1), $r8 = virtualinvoke $r7.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(") = "), $r7 = virtualinvoke $r6.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i1), $r6 = virtualinvoke $r5.<java.lang.StringBuilder: java.lang.StringBuilder append(java.lang.String)>(", "), $r5 = virtualinvoke $r3.<java.lang.StringBuilder: java.lang.StringBuilder append(int)>(i0), specialinvoke $r3.<java.lang.StringBuilder: void <init>(java.lang.String)>("gcd("), $r3 = new java.lang.StringBuilder, $r4 = <java.lang.System: java.io.PrintStream out>, i1 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r2), $r2 = r0[1], i0 = staticinvoke <java.lang.Integer: int parseInt(java.lang.String)>($r1),  $r1 = r0[0], if $i2 >= 2 goto $r1 = r0[0], r0 := @parameter0: java.lang.String[], $i2 = lengthof r0, and itself

Then, there is a new control graph for the next method.

i0 := @parameter0: int is dominated by itself

i1 := @parameter1: int is dominated by i0 := @parameter0: int and itself

if i0 <= i1 goto i8 = i0 is dominated by i1 := @parameter1: int,  i0 := @parameter0: int, and itself

i7 = i1 is dominated by if i0 <= i1 goto i8 = i0,  i1 := @parameter1: int,  i0 := @parameter0: int, and itself

goto [?= (branch)] is dominated by i7 = i1, if i0 <= i1 goto i8 = i0,  i1 := @parameter1: int,  i0 := @parameter0: int, and itself

$i5 = i0 % i7 is dominated by goto [?= (branch)], if i7 >= 1 goto $i5 = i0 % i7, i7 = i1, if i0 <= i1 goto i8 = i0,  i1 := @parameter1: int,  i0 := @parameter0: int, and itself

if $i5 != 0 goto i7 = i7 + -1 is dominated by $i5 = i0 % i7, goto [?= (branch)], if i7 >= 1 goto $i5 = i0 % i7, i7 = i1, if i0 <= i1 goto i8 = i0,  i1 := @parameter1: int,  i0 := @parameter0: int, and itself

$i6 = i1 % i7 is dominated by if $i5 != 0 goto i7 = i7 + -1, $i5 = i0 % i7, goto [?= (branch)], if i7 >= 1 goto $i5 = i0 % i7, i7 = i1, if i0 <= i1 goto i8 = i0,  i1 := @parameter1: int,  i0 := @parameter0: int, and itself

if $i6 != 0 goto i7 = i7 + -1 is dominated by $i6 = i1 % i7,  if $i5 != 0 goto i7 = i7 + -1, $i5 = i0 % i7, goto [?= (branch)], if i7 >= 1 goto $i5 = i0 % i7, i7 = i1, if i0 <= i1 goto i8 = i0,  i1 := @parameter1: int,  i0 := @parameter0: int, and itself

return i7 is dominated by if $i6 != 0 goto i7 = i7 + -1,  $i6 = i1 % i7,  if $i5 != 0 goto i7 = i7 + -1, $i5 = i0 % i7, goto [?= (branch)], if i7 >= 1 goto $i5 = i0 % i7, i7 = i1, if i0 <= i1 goto i8 = i0,  i1 := @parameter1: int,  i0 := @parameter0: int, and itself

i7 = i7 + -1 is dominated by if $i5 != 0 goto i7 = i7 + -1, $i5 = i0 % i7, goto [?= (branch)], if i7 >= 1 goto $i5 = i0 % i7, i7 = i1, if i0 <= i1 goto i8 = i0,  i1 := @parameter1: int,  i0 := @parameter0: int, and itself

if i7 >= 1 goto $i5 = i0 % i7 is dominated by goto [?= (branch)], i7 = i1, if i0 <= i1 goto i8 = i0,  i1 := @parameter1: int,  i0 := @parameter0: int, and itself

goto [?= return 1] is dominated by if i7 >= 1 goto $i5 = i0 % i7, goto [?= (branch)], i7 = i1, if i0 <= i1 goto i8 = i0,  i1 := @parameter1: int,  i0 := @parameter0: int, and itself

i8 = i0 is dominated by if i0 <= i1 goto i8 = i0,  i1 := @parameter1: int,  i0 := @parameter0: int, and itself because of the else statement

goto [?= (branch)] is dominated by i8 = i0, if i0 <= i1 goto i8 = i0,  i1 := @parameter1: int,  i0 := @parameter0: int, and itself

$i3 = i0 % i8 is dominated by goto [?= (branch)], if i8 >= 1 goto $i3 = i0 % i8, i8 = i0, if i0 <= i1 goto i8 = i0,  i1 := @parameter1: int,  i0 := @parameter0: int, and itself 

if $i3 != 0 goto i8 = i8 + -1 is dominated by $i3 = i0 % i8, goto [?= (branch)], if i8 >= 1 goto $i3 = i0 % i8, i8 = i0, if i0 <= i1 goto i8 = i0,  i1 := @parameter1: int,  i0 := @parameter0: int, and itself 

$i4 = i1 % i8 is dominated by if $i3 != 0 goto i8 = i8 + -1, $i3 = i0 % i8, goto [?= (branch)], if i8 >= 1 goto $i3 = i0 % i8, i8 = i0, if i0 <= i1 goto i8 = i0,  i1 := @parameter1: int,  i0 := @parameter0: int, and itself 

if $i4 != 0 goto i8 = i8 + -1 is dominated by $i4 = i1 % i8, if $i3 != 0 goto i8 = i8 + -1, $i3 = i0 % i8, goto [?= (branch)], if i8 >= 1 goto $i3 = i0 % i8, i8 = i0, if i0 <= i1 goto i8 = i0,  i1 := @parameter1: int,  i0 := @parameter0: int, and itself 

return i8 is dominated by if $i4 != 0 goto i8 = i8 + -1, $i4 = i1 % i8, if $i3 != 0 goto i8 = i8 + -1, $i3 = i0 % i8, goto [?= (branch)], if i8 >= 1 goto $i3 = i0 % i8, i8 = i0, if i0 <= i1 goto i8 = i0,  i1 := @parameter1: int,  i0 := @parameter0: int, and itself 

i8 = i8 + -1 is dominated by if $i3 != 0 goto i8 = i8 + -1, $i3 = i0 % i8, goto [?= (branch)], if i8 >= 1 goto $i3 = i0 % i8, i8 = i0, if i0 <= i1 goto i8 = i0,  i1 := @parameter1: int,  i0 := @parameter0: int, and itself 

if i8 >= 1 goto $i3 = i0 % i8 is dominated by goto [?= (branch)], if i8 >= 1 goto $i3 = i0 % i8, i8 = i0, if i0 <= i1 goto i8 = i0,  i1 := @parameter1: int,  i0 := @parameter0: int, and itself 

return 1 is dominated by if i0 <= i1 goto i8 = i0,  i1 := @parameter1: int,  i0 := @parameter0: int, and itself

