# TARGETS
# target: dependencies
#		commands
#

DEBUG = 1
EXECUTABLE_FILENAME = main

CXX_STANDARD = c++17
CXX_WARNINGS = -Wall -Wextra -Wpedantic
CXX = g++
CXXFLAGS = $(CXX_WARNINGS) -std=$(CXX_STANDARD)
LDFLAGS =

ifeq ($(DEBUG), 1)
CXXFLAGS += -g -O0
else
CXXFLAGS += -O3
endif

COMPILER_CALL = $(CXX) $(CXXFLAGS)


build: main.o lib.o
	$(COMPILER_CALL) main.o lib.o $(LDFLAGS) -o $(EXECUTABLE_FILENAME)

main.o:
	$(COMPILER_CALL) -c main.cc

lib.o:
	$(COMPILER_CALL) -c lib.cc

execute:
	./main

clean:
	rm -f *.o
	rm -f main
