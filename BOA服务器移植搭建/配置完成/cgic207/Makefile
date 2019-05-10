CFLAGS=-g -Wall
CC=sw_64sw2-unknown-linux-gnu-gcc
AR=sw_64sw2-unknown-linux-gnu-ar
RANLIB=sw_64sw2-unknown-linux-gnu-ranlib
LIBS=-L./ -lcgic

all: libcgic.a cgictest.cgi capture

install: libcgic.a
	cp libcgic.a /usr/local/lib
	cp cgic.h /usr/local/include
	@echo libcgic.a is in /usr/local/lib. cgic.h is in /usr/local/include.

libcgic.a: cgic.o cgic.h
	rm -f libcgic.a
	$(AR) rc libcgic.a cgic.o
	$(RANLIB) libcgic.a

#mingw32 and cygwin users: replace .cgi with .exe

cgictest.cgi: cgictest.o libcgic.a
	$(CC) $(CFLAGS) cgictest.o -o cgictest.cgi ${LIBS}

capture: capture.o libcgic.a
	$(CC) $(CFLAGS) capture.o -o capture ${LIBS}

clean:
	rm -f *.o *.a cgictest.cgi capture cgicunittest

test:
	gcc -D UNIT_TEST=1 cgic.c -o cgicunittest
	./cgicunittest
