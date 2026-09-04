| Núcleos activos | Tiempo real (s) | Speedup S=T1/Tn | Eficiencia E=S/N | Estim. fracción paralela (Amdahl) |
|:---:|---:|---:|---:|---:|
| 1 | 23.661 | 1.000 | 1.00 | — |
| 2 | 20.656 | 1.146 | 0.573 | 0.25 |
| 3 | 17.718 | 1.336 | 0.445 | 0.38 |
| 4 | 14.783 | 1.600 | 0.400 | 0.50 |
| 5 | 11.869 | 1.995 | 0.399 | 0.62 |
| 6 | 8.890 | 2.663 | 0.444 | 0.75 |
| 7 | 5.975 | 3.959 | 0.566 | 0.87 |
| 8 | 3.165 | 7.479 | 0.935 | 0.99 |

![cpu-affinity](Images/Figure_1.png)

```bash
roussel@desk:~/Desktop/practica-clase-sem4/semana 3/threading$ make
gcc -Wall -Wextra -O3 cpu-naive.c -o cpu-naive -pthread
gcc -Wall -Wextra -O3 cpu-affinity.c -o cpu-affinity -pthread
roussel@desk:~/Desktop/practica-clase-sem4/semana 3/threading$ time ./cpu-affinity
CPUs logicos disponibles: 16
Thread 2: 256.00 MB inicializados desde CPU 0
Thread 4: 256.00 MB inicializados desde CPU 0
Thread 3: 256.00 MB inicializados desde CPU 0
Thread 6: 256.00 MB inicializados desde CPU 0
Thread 0: 256.00 MB inicializados desde CPU 0
Thread 5: 256.00 MB inicializados desde CPU 0
Thread 1: 256.00 MB inicializados desde CPU 0
Thread 7: 256.00 MB inicializados desde CPU 0
Thread 0: finalizado en CPU 0
Thread 7: finalizado en CPU 0
Thread 3: finalizado en CPU 0
Thread 4: finalizado en CPU 0
Thread 2: finalizado en CPU 0
Thread 5: finalizado en CPU 0
Thread 1: finalizado en CPU 0
Thread 6: finalizado en CPU 0

real    0m23.661s
user    0m22.796s
sys     0m0.864s
roussel@desk:~/Desktop/practica-clase-sem4/semana 3/threading$ make
gcc -Wall -Wextra -O3 cpu-affinity.c -o cpu-affinity -pthread
roussel@desk:~/Desktop/practica-clase-sem4/semana 3/threading$ time ./cpu-affinity
CPUs logicos disponibles: 16
Thread 1: 256.00 MB inicializados desde CPU 1
Thread 4: 256.00 MB inicializados desde CPU 0
Thread 0: 256.00 MB inicializados desde CPU 0
Thread 2: 256.00 MB inicializados desde CPU 0
Thread 5: 256.00 MB inicializados desde CPU 0
Thread 6: 256.00 MB inicializados desde CPU 0
Thread 3: 256.00 MB inicializados desde CPU 0
Thread 7: 256.00 MB inicializados desde CPU 0
Thread 1: finalizado en CPU 1
Thread 4: finalizado en CPU 0
Thread 0: finalizado en CPU 0
Thread 2: finalizado en CPU 0
Thread 5: finalizado en CPU 0
Thread 6: finalizado en CPU 0
Thread 3: finalizado en CPU 0
Thread 7: finalizado en CPU 0

real    0m20.656s
user    0m22.718s
sys     0m0.895s
roussel@desk:~/Desktop/practica-clase-sem4/semana 3/threading$ make
make: Nothing to be done for 'all'.
roussel@desk:~/Desktop/practica-clase-sem4/semana 3/threading$ make
gcc -Wall -Wextra -O3 cpu-affinity.c -o cpu-affinity -pthread
roussel@desk:~/Desktop/practica-clase-sem4/semana 3/threading$ time ./cpu-affinity
CPUs logicos disponibles: 16
Thread 1: 256.00 MB inicializados desde CPU 1
Thread 2: 256.00 MB inicializados desde CPU 2
Thread 5: 256.00 MB inicializados desde CPU 0
Thread 4: 256.00 MB inicializados desde CPU 0
Thread 3: 256.00 MB inicializados desde CPU 0
Thread 0: 256.00 MB inicializados desde CPU 0
Thread 7: 256.00 MB inicializados desde CPU 0
Thread 6: 256.00 MB inicializados desde CPU 0
Thread 2: finalizado en CPU 2
Thread 1: finalizado en CPU 1
Thread 0: finalizado en CPU 0
Thread 3: finalizado en CPU 0
Thread 4: finalizado en CPU 0
Thread 5: finalizado en CPU 0
Thread 6: finalizado en CPU 0
Thread 7: finalizado en CPU 0

real    0m17.718s
user    0m22.733s
sys     0m0.914s
roussel@desk:~/Desktop/practica-clase-sem4/semana 3/threading$ make
gcc -Wall -Wextra -O3 cpu-affinity.c -o cpu-affinity -pthread
roussel@desk:~/Desktop/practica-clase-sem4/semana 3/threading$ time ./cpu-affinity
CPUs logicos disponibles: 16
Thread 2: 256.00 MB inicializados desde CPU 2
Thread 1: 256.00 MB inicializados desde CPU 1
Thread 3: 256.00 MB inicializados desde CPU 3
Thread 7: 256.00 MB inicializados desde CPU 0
Thread 6: 256.00 MB inicializados desde CPU 0
Thread 0: 256.00 MB inicializados desde CPU 0
Thread 4: 256.00 MB inicializados desde CPU 0
Thread 5: 256.00 MB inicializados desde CPU 0
Thread 2: finalizado en CPU 2
Thread 3: finalizado en CPU 3
Thread 1: finalizado en CPU 1
Thread 6: finalizado en CPU 0
Thread 0: finalizado en CPU 0
Thread 5: finalizado en CPU 0
Thread 4: finalizado en CPU 0
Thread 7: finalizado en CPU 0

real    0m14.783s
user    0m22.749s
sys     0m0.935s
roussel@desk:~/Desktop/practica-clase-sem4/semana 3/threading$ make
gcc -Wall -Wextra -O3 cpu-affinity.c -o cpu-affinity -pthread
roussel@desk:~/Desktop/practica-clase-sem4/semana 3/threading$ time ./cpu-affinity
CPUs logicos disponibles: 16
Thread 4: 256.00 MB inicializados desde CPU 4
Thread 3: 256.00 MB inicializados desde CPU 3
Thread 1: 256.00 MB inicializados desde CPU 1
Thread 2: 256.00 MB inicializados desde CPU 2
Thread 0: 256.00 MB inicializados desde CPU 0
Thread 5: 256.00 MB inicializados desde CPU 0
Thread 7: 256.00 MB inicializados desde CPU 0
Thread 6: 256.00 MB inicializados desde CPU 0
Thread 3: finalizado en CPU 3
Thread 4: finalizado en CPU 4
Thread 2: finalizado en CPU 2
Thread 1: finalizado en CPU 1
Thread 6: finalizado en CPU 0
Thread 0: finalizado en CPU 0
Thread 7: finalizado en CPU 0
Thread 5: finalizado en CPU 0

real    0m11.869s
user    0m22.860s
sys     0m0.910s
roussel@desk:~/Desktop/practica-clase-sem4/semana 3/threading$ make
gcc -Wall -Wextra -O3 cpu-affinity.c -o cpu-affinity -pthread
roussel@desk:~/Desktop/practica-clase-sem4/semana 3/threading$ time ./cpu-affinity
CPUs logicos disponibles: 16
Thread 1: 256.00 MB inicializados desde CPU 1
Thread 3: 256.00 MB inicializados desde CPU 3
Thread 4: 256.00 MB inicializados desde CPU 4
Thread 2: 256.00 MB inicializados desde CPU 2
Thread 5: 256.00 MB inicializados desde CPU 5
Thread 0: 256.00 MB inicializados desde CPU 0
Thread 6: 256.00 MB inicializados desde CPU 0
Thread 7: 256.00 MB inicializados desde CPU 0
Thread 3: finalizado en CPU 3
Thread 4: finalizado en CPU 4
Thread 2: finalizado en CPU 2
Thread 5: finalizado en CPU 5
Thread 1: finalizado en CPU 1
Thread 0: finalizado en CPU 0
Thread 7: finalizado en CPU 0
Thread 6: finalizado en CPU 0

real    0m8.890s
user    0m22.840s
sys     0m0.974s
roussel@desk:~/Desktop/practica-clase-sem4/semana 3/threading$ make
gcc -Wall -Wextra -O3 cpu-affinity.c -o cpu-affinity -pthread
roussel@desk:~/Desktop/practica-clase-sem4/semana 3/threading$ time ./cpu-affinity
CPUs logicos disponibles: 16
Thread 2: 256.00 MB inicializados desde CPU 2
Thread 5: 256.00 MB inicializados desde CPU 5
Thread 3: 256.00 MB inicializados desde CPU 3
Thread 4: 256.00 MB inicializados desde CPU 4
Thread 1: 256.00 MB inicializados desde CPU 1
Thread 6: 256.00 MB inicializados desde CPU 6
Thread 0: 256.00 MB inicializados desde CPU 0
Thread 7: 256.00 MB inicializados desde CPU 0
Thread 2: finalizado en CPU 2
Thread 5: finalizado en CPU 5
Thread 3: finalizado en CPU 3
Thread 4: finalizado en CPU 4
Thread 6: finalizado en CPU 6
Thread 1: finalizado en CPU 1
Thread 7: finalizado en CPU 0
Thread 0: finalizado en CPU 0

real    0m5.975s
user    0m22.929s
sys     0m1.015s
roussel@desk:~/Desktop/practica-clase-sem4/semana 3/threading$ make
gcc -Wall -Wextra -O3 cpu-affinity.c -o cpu-affinity -pthread
roussel@desk:~/Desktop/practica-clase-sem4/semana 3/threading$ time ./cpu-affinity
CPUs logicos disponibles: 16
Thread 6: 256.00 MB inicializados desde CPU 6
Thread 0: 256.00 MB inicializados desde CPU 0
Thread 2: 256.00 MB inicializados desde CPU 2
Thread 4: 256.00 MB inicializados desde CPU 4
Thread 7: 256.00 MB inicializados desde CPU 7
Thread 3: 256.00 MB inicializados desde CPU 3
Thread 5: 256.00 MB inicializados desde CPU 5
Thread 1: 256.00 MB inicializados desde CPU 1
Thread 6: finalizado en CPU 6
Thread 3: finalizado en CPU 3
Thread 4: finalizado en CPU 4
Thread 5: finalizado en CPU 5
Thread 7: finalizado en CPU 7
Thread 2: finalizado en CPU 2
Thread 1: finalizado en CPU 1
Thread 0: finalizado en CPU 0

real    0m3.165s
user    0m23.080s
sys     0m1.117s
