PORTNAME=	ffms2
DISTVERSION=	2.40
PORTREVISION=	3
CATEGORIES=	multimedia

PATCH_SITES=	https://github.com/${GH_ACCOUNT}/${GH_PROJECT}/commit/
PATCHFILES+=	96cbf38ea938.patch:-p1 # https://github.com/FFMS/ffms2/pull/380
PATCHFILES+=	586d87de3f89.patch:-p1 # https://github.com/FFMS/ffms2/pull/380
PATCHFILES+=	45673149e9a2.patch:-p1 # https://github.com/FFMS/ffms2/pull/380

MAINTAINER=	jbeich@FreeBSD.org
COMMENT=	FFmpeg-based source library and VapourSynth plugin
WWW=		https://github.com/FFMS/ffms2

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/COPYING

BUILD_DEPENDS=	${LOCALBASE}/include/vapoursynth/VSHelper.h:multimedia/vapoursynth
LIB_DEPENDS=	libavcodec.so:multimedia/ffmpeg

USE_GITHUB=	yes
GH_ACCOUNT=	FFMS

USES=		autoreconf compiler:c++11-lib gmake libtool pathfix pkgconfig
EXCLUDE=	VSHelper.h VSScript.h VapourSynth.h
EXTRACT_AFTER_ARGS=${EXCLUDE:S,^,--exclude ,}
GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--enable-static
CPPFLAGS+=	`pkg-config vapoursynth --cflags`
INSTALL_TARGET=	install-strip
USE_LDCONFIG=	yes
DATADIR=	${PREFIX}/lib/vapoursynth

OPTIONS_DEFINE=	DOCS

pre-configure:
	@${MKDIR} ${WRKSRC}/src/config # from autogen.sh

post-patch:
	@${REINPLACE_CMD} -e '/^dist_doc_DATA/s,=,& \
			doc/${PORTNAME}-vapoursynth.md,' \
		${WRKSRC}/Makefile.am

post-install:
	${MKDIR} ${STAGEDIR}${DATADIR}
	${LN} -sf ../lib${PORTNAME}.so ${STAGEDIR}${DATADIR}/

.include <bsd.port.mk>
