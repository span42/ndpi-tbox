NDPI_PATH2 := ${NDPI_PATH}/src
NDPI_SRC := ndpi_cpy
NDPI_PRO := ${NDPI_SRC}/lib/protocols

CFLAGS = -fPIC -I/opt/tbox/gcc-4.4.6-glibc-2.9/arm-926ejs-linux-gnueabi/arm-926ejs-linux-gnueabi/usr/include    -I${NDPI_SRC}/include -I${NDPI_SRC}/lib -I../src -DOPENDPI_NETFILTER_MODULE -O2 -Wall -DNDPI_IPTABLES_EXT

all:
	if test -d ${NDPI_SRC}; then \
		cp ${NDPI_PATH2}/* ${NDPI_SRC} -R; \
	else \
		mkdir ${NDPI_SRC}; \
		cp ${NDPI_PATH2}/* ${NDPI_SRC} -R; \
	fi
	cp ${NDPI_SRC}/../../nDPI-patch/src/* ${NDPI_SRC}/ -R;
	make libxt_ndpi.so
	rm -r ${NDPI_SRC}
lib%.so: lib%.o
	$(CC) -shared -o $@ $^;
lib%.o: lib%.c
	$(CC) ${CFLAGS} -D_INIT=lib$*_init -c -o $@ $<;
clean:
	rm -rf libxt_ndpi.so ${NDPI_SRC}
