# Compiler
CC = gcc

# Directories
BUILD = build
BIN = bin
SRC = src
INC = include

# Install prefix (Linux + Termux safe)
PREFIX ?= $(HOME)/.local
BINDIR = $(PREFIX)/bin

TARGET = $(BIN)/ema
APPNAME = ema

# Object files
OBJS = \
	$(BUILD)/main.o \
	$(BUILD)/contactor.o \
	$(BUILD)/manager.o \
	$(BUILD)/emails.o \
	$(BUILD)/names.o \
	$(BUILD)/memory.o \
	$(BUILD)/user.o

# Default target
all: $(TARGET)

# Link
$(TARGET): $(OBJS)
	mkdir -p $(BIN)
	$(CC) -I$(INC) $(OBJS) -o $(TARGET)

# Compile rules
$(BUILD)/%.o: $(SRC)/%.c
	mkdir -p $(BUILD)
	$(CC) -I$(INC) -c $< -o $@

# Install
install: $(TARGET)
	mkdir -p $(BINDIR)
	cp $(TARGET) $(BINDIR)/$(APPNAME)
	chmod +x $(BINDIR)/$(APPNAME)
	@echo "Installed to $(BINDIR)/$(APPNAME)"

# Uninstall
uninstall:
	rm -f $(BINDIR)/$(APPNAME)
	@echo "Removed $(BINDIR)/$(APPNAME)"

# Clean (preserve saves/)
clean:
	rm -rf $(BUILD) $(BIN)
