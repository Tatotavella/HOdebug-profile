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