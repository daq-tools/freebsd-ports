PORTNAME=	fnc
DISTVERSION=	0.13
CATEGORIES=	devel
MASTER_SITES=	https://fnc.bsdbox.org/tarball/${DISTVERSION}/ \
		https://distfiles.pirateparty.in/ashish/

MAINTAINER=	ashish@FreeBSD.org
COMMENT=	Interactive ncurses browser for Fossil repositories
WWW=		https://fnc.bsdbox.org/

LICENSE=	ISCL
LICENSE_FILE=	${WRKSRC}/LICENSE

USES=		ncurses

PLIST_FILES=	bin/fnc \
		man/man1/fnc.1.gz

# For patch application
post-extract:
	${REINPLACE_CMD} -e '/^VERSION/s/${DISTVERSION}$$/%%VERSION%%/' \
		${WRKSRC}/fnc.bld.mk

pre-build:
	${REINPLACE_CMD} -e '/^VERSION/s/%%VERSION%%/${DISTVERSION}$$/' \
		${WRKSRC}/fnc.bld.mk

.include <bsd.port.mk>
