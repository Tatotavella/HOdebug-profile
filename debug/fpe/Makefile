.PHONY: default help object executable all clean
CC = gcc 
CFLAGS = -g -Wall -DTRAPFPE 
LDFLAGS = -lm
LD = $(CC)
INC = -I/home/alumno/Escritorio/WTPC/HOdebug-profile/debug/fpe/fpe_x87_sse

FPE_DIR = /home/alumno/Escritorio/WTPC/HOdebug-profile/debug/fpe/fpe_x87_sse
SOURCE_C = $(wildcard *.c)
OBJECTS_C = $(patsubst %.c, %_c.o, $(SOURCE_C))

OBJECTS_FPE = $(patsubst $(FPE_DIR)/%.c, %_c.o, $(SOURCE_C))

EXECUTABLES = $(patsubst %.c, %.e, $(SOURCE_C))

default: all

help:
	@echo "\
  make all:           make every executable (default)\n\
  make clean:         delete output files\n\
  make help:          display this help"

objects: $(OBJECTS_C)

objects_fpe: $(OBJECTS_FPE)

executable: $(EXECUTABLES)

all: objects objects_fpe executable

%_c.o: %.c
	$(CC) $(INC) $(CFLAGS) -c $^ -o $@ 

$(FPE_DIR)/%_c.o : $(FPE_DIR)/%.c
	$(CC) $(CFLAGS) -c $^ -o $@

%.e: %_c.o
	$(LD) $^ -o $@ $(LDFLAGS) 

clean:
	rm -rfv $(OBJECTS_C) $(EXECUTABLES)
