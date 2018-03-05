Profile
Antes que nada fue necesario setear ulimit -s unlimited porque porque profile_me_1 generaba una violacion del segmento core
Resultados de C/profile_me_1.c con time
-O0
real	0m4.100s
user	0m3.752s
sys	0m0.340s

-O1
real	0m3.878s
user	0m3.592s
sys	0m0.280s

-O2
real	0m3.896s
user	0m3.620s
sys	0m0.272s

-O3
real	0m0.002s
user	0m0.000s
sys	0m0.000s

Con gprof primero debemos compilar y linkear el programa con la flag -pg y luego correrlo para que genere un archivo llamado gmon.out 
Luego corremos gprof ./prog.e y nos aparecen los datos del profiling. Una buena característica es que aparecen la cantidad de veces que cada función es llamada y cuánto tiempo se consume en cada una de ellas.

-O0
Each sample counts as 0.01 seconds.
  %   cumulative   self              self     total           
 time   seconds   seconds    calls  ns/call  ns/call  name    
 85.43      5.16     5.16 25000000   206.40   206.40  first_assign
 10.26      5.78     0.62                             main
  4.30      6.04     0.26 25000000    10.40    10.40  second_assign

index % time    self  children    called     name
                                                 <spontaneous>
[1]    100.0    0.62    5.42                 main [1]
                5.16    0.00 25000000/25000000     first_assign [2]
                0.26    0.00 25000000/25000000     second_assign [3]
-----------------------------------------------
                5.16    0.00 25000000/25000000     main [1]
[2]     85.4    5.16    0.00 25000000         first_assign [2]
-----------------------------------------------
                0.26    0.00 25000000/25000000     main [1]
[3]      4.3    0.26    0.00 25000000         second_assign [3]
-----------------------------------------------

 -O1
  %   cumulative   self              self     total           
 time   seconds   seconds    calls  ns/call  ns/call  name    
 88.25      5.18     5.18 25000000   207.20   207.20  first_assign
  7.67      5.63     0.45                             main
  4.09      5.87     0.24 25000000     9.60     9.60  second_assign

index % time    self  children    called     name
                                                 <spontaneous>
[1]    100.0    0.45    5.42                 main [1]
                5.18    0.00 25000000/25000000     first_assign [2]
                0.24    0.00 25000000/25000000     second_assign [3]
-----------------------------------------------
                5.18    0.00 25000000/25000000     main [1]
[2]     88.2    5.18    0.00 25000000         first_assign [2]
-----------------------------------------------
                0.24    0.00 25000000/25000000     main [1]
[3]      4.1    0.24    0.00 25000000         second_assign [3]
-----------------------------------------------

-O2
  %   cumulative   self              self     total           
 time   seconds   seconds    calls  Ts/call  Ts/call  name    
 95.68      5.32     5.32                             first_assign
  4.32      5.56     0.24                             second_assign

-O3
 no time accumulated

