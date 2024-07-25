# TARGETS
# target: dependencies
#		commands
#

INCLUDE_DIR = include
SOURCE_DIR = src
BUILD_DIR = build
DEBUG = 1
ENABLE_WARNINGS = 1
WARNINGS_AS_ERRORS = 0

CXX_STANDARD = c++17
ifeq ($(ENABLE_WARNINGS), 1)
	CXX_WARNINGS = -Wall -Wextra -Wpedantic
else
	CXX_WARNINGS =
endif
ifeq ($(WARNINGS_AS_ERRORS), 1)
	CXX_WARNINGS += -Werror
endif

CXX = g++
CPPFLAGS = -I $(INCLUDE_DIR)
CXXFLAGS = $(CXX_WARNINGS) -std=$(CXX_STANDARD)
LDFLAGS =

ifeq ($(DEBUG), 1)
	CXXFLAGS += -g -O0
	EXECUTABLE_FILENAME = mainDebug
else
	CXXFLAGS += -O3
	EXECUTABLE_FILENAME = mainRelease
endif

CXX_COMPILER_CALL = $(CXX) $(CXXFLAGS) $(CPPFLAGS)
CXX_SOURCES = $(wildcard $(SOURCE_DIR)/*.cc)
CXX_OBJECTS = $(patsubst $(SOURCE_DIR)/%.cc, $(BUILD_DIR)/%.o, $(CXX_SOURCES))

create_build_folder:
	@mkdir -p build

build: create_build_folder $(CXX_OBJECTS)
	$(CXX_COMPILER_CALL) $(CXX_OBJECTS) $(LDFLAGS) -o $(BUILD_DIR)/$(EXECUTABLE_FILENAME)

execute:
	./$(BUILD_DIR)/$(EXECUTABLE_FILENAME)

clean:
	rm -f $(BUILD_DIR)/*.o
	rm -f $(BUILD_DIR)/$(EXECUTABLE_FILENAME)

##############
## PATTERNS ##
##############
# $@: the file name of the target
# $<: the name of the first dependency
# $^: the names of all prerequisites

$(BUILD_DIR)/%.o: $(SOURCE_DIR)/%.cc
	$(CXX_COMPILER_CALL) -c $< -o $@

###########
## PHONY ##
###########
.PHONY: create_build_folder build execute clean
