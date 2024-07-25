# TARGETS
# target: dependencies
#		commands
#

DEBUG = 1

CXX_STANDARD = c++17
CXX_WARNINGS = -Wall -Wextra -Wpedantic
CXX = g++
CXXFLAGS = $(CXX_WARNINGS) -std=$(CXX_STANDARD)
LDFLAGS =

ifeq ($(DEBUG), 1)
CXXFLAGS += -g -O0
EXECUTABLE_FILENAME = mainDebug
else
CXXFLAGS += -O3
EXECUTABLE_FILENAME = mainRelease
endif

CXX_COMPILER_CALL = $(CXX) $(CXXFLAGS)
CXX_SOURCES = $(wildcard *.cc)
CXX_OBJECTS = $(patsubst %.cc, %.o, $(CXX_SOURCES))


build: $(CXX_OBJECTS)
	$(CXX_COMPILER_CALL) $(CXX_OBJECTS) $(LDFLAGS) -o $(EXECUTABLE_FILENAME)

execute:
	./$(EXECUTABLE_FILENAME)

clean:
	rm -f *.o
	rm -f $(EXECUTABLE_FILENAME)

##############
## PATTERNS ##
##############
# $@: the file name of the target
# $<: the name of the first dependency
# $^: the names of all prerequisites

*.o: *.cc
	$(CXX_COMPILER_CALL) -c $<
