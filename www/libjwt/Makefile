PORTNAME=	libjwt
PORTVERSION=	1.15.2
DISTVERSIONPREFIX=	v
CATEGORIES=	www

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	JSON Web Token implementation in C
WWW=		https://github.com/benmcollins/libjwt

LICENSE=	MPL20
LICENSE_FILE=	${WRKSRC}/LICENSE

BUILD_DEPENDS=	jansson>=2.0:devel/jansson
LIB_DEPENDS=	libjansson.so:devel/jansson
TEST_DEPENDS=	check>=0.9.4:devel/check

USES=		autoreconf gmake libtool pathfix pkgconfig ssl

CONFIGURE_ENV=	OPENSSL_CFLAGS="-I${OPENSSLINC}" \
		OPENSSL_LIBS="-L${OPENSSLLIB} -lcrypto -lssl"
GNU_CONFIGURE=	yes
INSTALL_TARGET=	install-strip
TEST_ARGS=	CFLAGS+=-I${LOCALBASE}/include LIBS+="-L${LOCALBASE}/lib -lcheck"
TEST_TARGET=	check
USE_LDCONFIG=	yes

USE_GITHUB=	yes
GH_ACCOUNT=	benmcollins

.include <bsd.port.mk>
