# Makefile for lua libs used by jivelite
# NB - repo has modified paths which assume use of luajit2.0 from source

TARGET   ?= linux
LD_FLAGS ?= "-shared"

LIBS = luasocket luazipfilter

all: $(LIBS)

luasocket: ../lib/lua/5.1/socket.so
luazipfilter: ../lib/lua/5.1/zipfilter.so

../lib/lua/5.1/socket.so:
	cd luasocket-2.0.2; make LD="gcc" PLATFORM=${TARGET}
	mkdir -p ../lib/lua/5.1
	cp luasocket-2.0.2/src/socket.so.2.0.2 ../lib/lua/5.1/socket.so
	cp luasocket-2.0.2/src/mime.so.1.0.2 ../lib/lua/5.1/mime.so

../lib/lua/5.1/zipfilter.so:
	cd luazipfilter; make MYLDFLAGS=${LD_FLAGS}
	mkdir -p ../lib/lua/5.1
	cp luazipfilter/zipfilter.so ../lib/lua/5.1/zipfilter.so

clean:
	cd luasocket-2.0.2; make PLATFORM=${TARGET} clean
	cd luazipfilter; make clean
	rm -f ../lib/lua/5.1/socket.so ../lib/lua/5.1/mime.so ../lib/lua/5.1/zipfilter.so

