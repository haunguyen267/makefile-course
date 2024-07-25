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

CXX_COMPILER_CALL = $(CXX) $(CXXFLAGS)
CXX_OBJECTS = main.o lib.o


build: $(CXX_OBJECTS)
	$(CXX_COMPILER_CALL) $(CXX_OBJECTS) $(LDFLAGS) -o $(EXECUTABLE_FILENAME)

execute:
	./main

clean:
	rm -f *.o
	rm -f main

##############
## PATTERNS ##
##############
# $@: the file name of the target
# $<: the name of the first dependency
# $^: the names of all prerequisites

*.o: *.cc
	$(CXX_COMPILER_CALL) -c $<
