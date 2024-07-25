# TARGETS
# target: dependencies
#		commands
#

build: main.o lib.o
	g++ main.o lib.o -o main

main.o:
	g++ -c main.cc

lib.o:
	g++ -c lib.cc

execute:
	./main

clean:
	rm -f *.o
	rm -f main
