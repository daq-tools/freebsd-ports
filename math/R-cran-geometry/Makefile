PORTNAME=	geometry
DISTVERSION=	0.4.6.1
PORTREVISION=	1
CATEGORIES=	math
DISTNAME=	${PORTNAME}_${DISTVERSION}

MAINTAINER=	tota@FreeBSD.org
COMMENT=	Mesh Generation and Surface Tesselation
WWW=		https://cran.r-project.org/web/packages/geometry/

LICENSE=	GPLv3

CRAN_DEPENDS=	R-cran-magic>0:math/R-cran-magic \
		R-cran-Rcpp>0:devel/R-cran-Rcpp \
		R-cran-lpSolve>0:math/R-cran-lpSolve \
		R-cran-linprog>0:math/R-cran-linprog \
		R-cran-RcppProgress>0:devel/R-cran-RcppProgress
BUILD_DEPENDS=	${CRAN_DEPENDS}
RUN_DEPENDS=	${CRAN_DEPENDS}

USES=		cran:auto-plist,compiles

.include <bsd.port.mk>
