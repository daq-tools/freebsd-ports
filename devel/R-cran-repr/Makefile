PORTNAME=	repr
PORTVERSION=	1.1.4
PORTREVISION=	1
CATEGORIES=	devel
DISTNAME=	${PORTNAME}_${PORTVERSION}

MAINTAINER=	tota@FreeBSD.org
COMMENT=	Serializable Reprensentations
WWW=		https://cran.r-project.org/web/packages/repr/

LICENSE=	GPLv3

CRAN_DEPENDS=	R-cran-htmltools>0:textproc/R-cran-htmltools \
		R-cran-jsonlite>0:converters/R-cran-jsonlite \
		R-cran-pillar>=1.4.0:devel/R-cran-pillar \
		R-cran-base64enc>0:converters/R-cran-base64enc
BUILD_DEPENDS=	${CRAN_DEPENDS}
RUN_DEPENDS=	${CRAN_DEPENDS}

USES=		cran:auto-plist

.include <bsd.port.mk>
