PORTNAME=	xarchiver
DISTVERSION=	0.5.4.20
PORTREVISION=	1
CATEGORIES=	archivers

MAINTAINER=	eduardo@FreeBSD.org
COMMENT=	Desktop-agnostic GTK frontend to various archiving tools
WWW=		https://github.com/ib/xarchiver

LICENSE=	GPLv2
LICENSE_FILE=	${WRKSRC}/COPYING

LIB_DEPENDS=	libfontconfig.so:x11-fonts/fontconfig \
		libfreetype.so:print/freetype2 \
		libharfbuzz.so:print/harfbuzz
RUN_DEPENDS=	7zz:archivers/7-zip \
		gtar:archivers/gtar \
		${LOCALBASE}/bin/gzip:archivers/gzip \
		${LOCALBASE}/bin/unzip:archivers/unzip \
		xdg-open:devel/xdg-utils \
		zip:archivers/zip

USES=		autoreconf desktop-file-utils gmake gnome libtool:build pkgconfig

USE_GITHUB=	yes
GH_ACCOUNT=	ib

USE_GNOME=	cairo gdkpixbuf2 glib20 intltool
GNU_CONFIGURE=	yes

PORTSCOUT=	limit:^\d\.\d\.\d\.\d+$ # avoid tags like identical_to_xfce_git_content

OPTIONS_DEFINE=	DOCS NLS
OPTIONS_GROUP=	FORMATS
OPTIONS_GROUP_FORMATS=	ARJ LZO RAR
OPTIONS_SINGLE=		GTK
OPTIONS_SINGLE_GTK=	GTK2 GTK3
OPTIONS_DEFAULT=	GTK3
OPTIONS_SUB=	yes

FORMATS_DESC=	Additional compression formats support
ARJ_DESC=	ARJ compression support
RAR_DESC=	RAR compression support

ARJ_RUN_DEPENDS=	arj:archivers/arj
LZO_RUN_DEPENDS=	lzop:archivers/lzop
RAR_RUN_DEPENDS=	unrar:archivers/unrar \
			rar:archivers/rar

DOCS_USE=		GNOME=libxslt
DOCS_CONFIGURE_ENABLE=	doc

GTK2_CONFIGURE_ENABLE=	gtk2
GTK2_USE=		GNOME=gtk20
GTK3_USE=		GNOME=gtk30

NLS_USES=	gettext localbase
NLS_USES_OFF=	gettext-tools
NLS_CONFIGURE_ENABLE=	nls

post-patch:
	@${REINPLACE_CMD} -e 's|%%LOCALBASE%%|${LOCALBASE}|g' \
		${WRKSRC}/src/main.c

post-patch-DOCS-off:
	@${REINPLACE_CMD} -e 's|doc||g' ${WRKSRC}/Makefile.in

post-patch-NLS-off:
	@${REINPLACE_CMD} -e 's| po | |g' ${WRKSRC}/Makefile.in

.include <bsd.port.mk>
