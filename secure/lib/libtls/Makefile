#	$OpenBSD: Makefile,v 1.37 2022/01/25 21:51:24 eric Exp $

.include "../libcrypto/Makefile.inc.libressl"

.if exists(Makefile.man)
.include "Makefile.man"
.endif

LTLS_SRC=	${LIBRESSL_SRC}/tls

CFLAGS+= -I${LTLS_SRC}
CFLAGS+= -I${LIBRESSL_SRC}/include

CFLAGS+= -Wall -Wimplicit -Wundef
.if ${COMPILER_TYPE:L} == "clang"
CFLAGS+= -Werror
.endif

LIB=	tls
SHLIB_MAJOR=	26

##LibreBSD: FreeBSD doesn't use DPADD / LDADD
LIBADD= crypto ssl

##LibreBSD: TODO
##LibreBSD: VERSION_SCRIPT=	Symbols.map
##LibreBSD: SYMBOL_LIST=	${.CURDIR}/Symbols.list

##LibreBSD: OpenBSD uses HDRS, FreeBSD uses INCS
INCS=	tls.h

SRCS=	tls.c \
	tls_bio_cb.c \
	tls_client.c \
	tls_config.c \
	tls_conninfo.c \
	tls_keypair.c \
	tls_peer.c \
	tls_server.c \
	tls_signer.c \
	tls_util.c \
	tls_ocsp.c \
	tls_verify.c

.PATH: ${LTLS_SRC} \
	${LIBRESSL_SRC}/include \
	${LIBRESSL_SRC}/man

.include <bsd.lib.mk>
