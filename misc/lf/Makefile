PORTNAME=	lf
DISTVERSIONPREFIX=	r
DISTVERSION=	28
PORTREVISION=	5
CATEGORIES=	misc

MAINTAINER=	yuri@FreeBSD.org
COMMENT=	Terminal file manager
WWW=		https://github.com/gokcehan/lf

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE

USES=		go:modules
USE_GITHUB=	yes
GH_ACCOUNT=	gokcehan
GH_TUPLE=	djherbis:times:v1.5.0:djherbis_times/vendor/github.com/djherbis/times \
		gdamore:encoding:v1.0.0:gdamore_encoding/vendor/github.com/gdamore/encoding \
		gdamore:tcell:d3cbfcfb7aa3:gdamore_tcell_v2/vendor/github.com/gdamore/tcell/v2 \
		golang:sys:8c9f86f7a55f:golang_sys/vendor/golang.org/x/sys \
		golang:term:03fcf44c2211:golang_term/vendor/golang.org/x/term \
		golang:text:v0.4.0:golang_text/vendor/golang.org/x/text \
		lucasb-eyer:go-colorful:v1.2.0:lucasb_eyer_go_colorful/vendor/github.com/lucasb-eyer/go-colorful \
		mattn:go-runewidth:v0.0.14:mattn_go_runewidth/vendor/github.com/mattn/go-runewidth \
		rivo:uniseg:v0.2.0:rivo_uniseg/vendor/github.com/rivo/uniseg
PLIST_FILES=	bin/lf

.include <bsd.port.mk>
