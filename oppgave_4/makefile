# TODO: Fjerne debug

INCLDIR = ./include
CC = gcc
CFLAGS = -O2
CFLAGS += -I$(INCLDIR)
LDFLAGS = -Wall -Wextra -g -O0 -I$(INCLDIR)
#LDFLAGS += -ansi -pedantic
OBJDIR = obj
DEBUGOBJSDIR = debugobjs

_DEPS = oppgave4.h
DEPS = $(patsubst %,$(INCLDIR)/%,$(_DEPS))

_OBJS = oppgave4.o main.o
OBJS = $(patsubst %,$(OBJDIR)/%,$(_OBJS))

_DEBUGOBJS = $(_OBJS)
DEBUGOBJS = $(patsubst %,$(DEBUGOBJSDIR)/%,$(_DEBUGOBJS))


$(OBJDIR)/%.o: %.c $(DEPS)
	$(CC) -c -o $@ $< $(CFLAGS)

$(DEBUGOBJSDIR)/%.o: %.c $(DEPS)
	$(CC) -c -o $@ $< $(LDFLAGS) -DDEBUG

oppgave4: $(OBJS)
	gcc -o $@ $^ $(CFLAGS)

debug: $(DEBUGOBJS)
	$(CC) -o $@ $^ $(LDFLAGS)

.PHONY: clean
clean:
	rm -f $(OBJDIR)/*.o
