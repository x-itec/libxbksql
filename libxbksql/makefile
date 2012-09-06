#ich musste die pg-lib vorher noch verlinken:
#ln -s /usr/local/lib/libpq.so /usr/lib/libpq.so

LIBVERSION=1
LIBSUBVERSION=0.0
LIBNAME=libxbkdbq

all:
	-rm debug.log
	cd src; \
	c++ -fPIC -g -c -I/usr/local/include/ -I/usr/local/include/mysql/ xbkdbq.cpp; \
	c++ -g -shared xbkdbq.o -L/usr/local/lib/mysql -lmysqlclient -lc -lpq  -Wl,-soname -Wl,${LIBNAME}.so.${LIBVERSION} -o ${LIBNAME}.so.${LIBVERSION}
	#c++ -g -Wall-lpq -lmysqlclient -shared -WL,-soname,${LIBNAME}.so.${LIBVERSION} -o ${LIBNAME}.so.${LIBVERSION}.${LIBSUBVERSION} xbkdbq.o -lc; \
	cp lib* /usr/local/lib;
	-ln -sf /usr/local/lib/${LIBNAME}.so.${LIBVERSION} /usr/lib/${LIBNAME}.so.${LIBVERSION};
	ln -sf /usr/lib/${LIBNAME}.so.${LIBVERSION} /usr/lib/${LIBNAME}${LIBVERSION}.so
	-mkdir /usr/include/xbk
	-cp include/*.h /usr/include/xbk
	-rm demo

demo:		
	c++ -c -I/usr/local/include -I/usr/local/include/mysql demo.cpp
	c++ -lbktest -o demo demo.o
	#c++ -lxbkdbq1 -o demo demo.o
