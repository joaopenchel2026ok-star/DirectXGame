CXX := g++
CXXFLAGS := -ld3d11 -ldxgi -ld3dcompiler -Wall -Wextra -std=c++20

# Automatically find all subdirectories in Include and add -I flags
INC_DIRS := $(shell find Include -type d)
INC_FLAGS := $(addprefix -I, $(INC_DIRS))

# Recursively find all .cpp files in Source
SRCS := $(shell find Source -name '*.cpp')

# Place object files in a build/ directory mirroring the Source structure
BUILD_DIR := build
OBJS := $(patsubst Source/%.cpp, $(BUILD_DIR)/%.o, $(SRCS))

TARGET := my_program.exe

# Default target
all: $(TARGET)

# Link all object files into the final executable
$(TARGET): $(OBJS)
	@mkdir -p $(dir $@)
	$(CXX) $(OBJS) -o $@ -ld3d11

# Compile Source files into build/ object files
$(BUILD_DIR)/%.o: Source/%.cpp
	@mkdir -p $(dir $@)
	$(CXX) $(CXXFLAGS) $(INC_FLAGS) -c $< -o $@

# Clean build artifacts
clean:
	rm -rf $(BUILD_DIR) $(TARGET)

.PHONY: all clean

