PLATFORM=gcc
include Makefile.in.$(PLATFORM)

EXES=hello.x demos.x

.PHONY: all hello2 hello4 clean

all: $(EXES)

hello2: hello.x
	OMP_NUM_THREADS=2 ./hello.x

hello4: hello.x
	OMP_NUM_THREADS=4 ./hello.x

%.x: %.o
	$(LD) $(LDFLAGS) $< -o $@ $(LIBS)

%.o: %.c
	$(CC) $(CFLAGS) -c $< 

demos.md: demos.c
	ldoc demos.c -o demos.md

demos.html: demos.md
	pandoc demos.md -o demos.html

clean:
	rm -f $(EXES)
