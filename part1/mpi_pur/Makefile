target: decide

CFLAGS=-g -O3 -std=c99
CC = mpicc

main.o: main.c projet.h master_slave.h
aux.o: aux.c projet.h
master_slave.o: master_slave.c master_slave.h projet.h 

decide: main.o aux.o master_slave.o
	$(CC) $(CFLAGS) $^ -o $@

exec: decide
	 mpirun -np 5 -hostfile hostfile --map-by node ./decide "4k//4K/4P w"

clean:
	rm -f *.o decide

.PHONY: clean
