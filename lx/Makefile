# Makefile for building a single directory of Java source files. It requires
# a DIR variable to be set.

BUILD_DIR := build
DIR := lx
SOURCES := $(wildcard $(DIR)/lox/*.java)
CLASSES := $(addprefix $(BUILD_DIR)/, $(SOURCES:.java=.class))
JAVA_OPTIONS := -Werror

clean:
	@ rm -r $(BUILD_DIR)/$(DIR)

default: generate_ast $(CLASSES)
	@: # Don't show "Nothing to be done" output.

generate_ast:
	@cd lx/tool && java GenerateAst.java ../lox

# Compile a single .java file to .class.
$(BUILD_DIR)/$(DIR)/%.class: $(DIR)/%.java
	@mkdir -p $(BUILD_DIR)/$(DIR)
	@javac -cp . -d $(BUILD_DIR)/$(DIR) $(JAVA_OPTIONS) -implicit:none $<
	@printf "%8s %-60s %s\n" javac $< "$(JAVA_OPTIONS)"

.PHONY: default clean
.DEFAULT_GOAL := default
