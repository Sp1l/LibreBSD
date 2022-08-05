#	$OpenBSD: Makefile,v 1.7 2015/09/11 21:07:01 beck Exp $

.include "../../lib/libcrypto/Makefile.inc.libressl"

PROG=	nc
SRCS=	netcat.c atomicio.c socks.c
##LibreBSD: FreeBSD doesn't use LDADD
LIBADD= tls ssl crypto

# Reset man-dir set for LibreSSL
MANDIR=	${SHAREDIR}/man/man
MAN1=	nc.1

## LibreSSL compat
SRCS+=	base64.c socket.c
CFLAGS+= -I${LIBRESSL_SRC}/apps/nc/compat
# readpassphrase.h
CFLAGS+=	-DHAVE_READPASSPHRASE_H
# sys/socket.h
CFLAGS+=	-DHAVE_ACCEPT4

.PATH:	${LIBRESSL_SRC}/apps/nc \
	${LIBRESSL_SRC}/apps/nc/compat

.include <bsd.prog.mk>
