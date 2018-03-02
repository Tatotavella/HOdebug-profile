.PHONY: default help object executable all clean
CC = gcc 
CFLAGS = -g -Wall -DTRAPFPE 
LDFLAGS = -lm
LD = $(CC)
FPE_DIR = ./fpe_x87_sse
INC = -I$(FPE_DIR)

SOURCE_C = $(wildcard *.c)
SOURCE_FPE = $(wildcard $(FPE_DIR)/*.c)
OBJECTS_C = $(patsubst %.c, %_c.o, $(SOURCE_C))
OBJECTS_FPE = $(patsubst %.c, %_c.o, $(SOURCE_FPE))
EXECUTABLES = $(patsubst %.c, %.e, $(SOURCE_C))

default: all

help:
	@echo "\
  make all:           make every executable (default)\n\
  make objects:           make every object\n\
  make clean:         delete output files\n\
  make help:          display this help"

objects: $(OBJECTS_C) $(OBJECTS_FPE)

executable: $(EXECUTABLES)

all: objects executable

%_c.o: %.c 
	$(CC) $(INC) $(CFLAGS) -c $^ -o $@ 

%.e: $(OBJECTS_FPE) %_c.o
	$(LD) $^ -o $@ $(LDFLAGS) 

clean:
	rm -rfv $(OBJECTS_C) $(OBJECTS_FPE) $(EXECUTABLES)
