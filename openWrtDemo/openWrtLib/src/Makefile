all:openWrtLib.o
	$(CC) -fPIC -shared -o libopenWrtLib.so openWrtLib.o

openWrtLib.o:openWrtLib.c openWrtLib.h
	$(CC) -fPIC -c -o openWrtLib.o openWrtLib.c

clean:
	rm -rf *.o *.a *.so