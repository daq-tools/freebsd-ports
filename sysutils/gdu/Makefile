PORTNAME=	gdu
DISTVERSIONPREFIX=	v
DISTVERSION=	5.22.0
PORTREVISION=	1
CATEGORIES=	sysutils

MAINTAINER=	lcook@FreeBSD.org
COMMENT=	Disk usage analyzer with console interface written in Go
WWW=		https://github.com/dundee/gdu

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE.md

USES=		go:modules,1.19
USE_GITHUB=	yes
GH_ACCOUNT=	dundee
GH_TUPLE=	davecgh:go-spew:v1.1.1:davecgh_go_spew/vendor/github.com/davecgh/go-spew \
		fatih:color:v1.13.0:fatih_color/vendor/github.com/fatih/color \
		gdamore:encoding:v1.0.0:gdamore_encoding/vendor/github.com/gdamore/encoding \
		gdamore:tcell:v2.5.3:gdamore_tcell_v2/vendor/github.com/gdamore/tcell/v2 \
		go-check:check:41f04d3bba15:go_check_check/vendor/gopkg.in/check.v1 \
		go-yaml:yaml:v3.0.1:go_yaml_yaml/vendor/gopkg.in/yaml.v3 \
		golang:sys:7b5979e65e41:golang_sys/vendor/golang.org/x/sys \
		golang:term:a9ba230a4035:golang_term/vendor/golang.org/x/term \
		golang:text:v0.3.7:golang_text/vendor/golang.org/x/text \
		inconshreveable:mousetrap:v1.0.1:inconshreveable_mousetrap/vendor/github.com/inconshreveable/mousetrap \
		kr:pretty:v0.3.0:kr_pretty/vendor/github.com/kr/pretty \
		lucasb-eyer:go-colorful:v1.2.0:lucasb_eyer_go_colorful/vendor/github.com/lucasb-eyer/go-colorful \
		maruel:natural:v1.1.0:maruel_natural/vendor/github.com/maruel/natural \
		mattn:go-colorable:v0.1.13:mattn_go_colorable/vendor/github.com/mattn/go-colorable \
		mattn:go-isatty:v0.0.16:mattn_go_isatty/vendor/github.com/mattn/go-isatty \
		mattn:go-runewidth:v0.0.13:mattn_go_runewidth/vendor/github.com/mattn/go-runewidth \
		pbnjay:memory:7b4eea64cf58:pbnjay_memory/vendor/github.com/pbnjay/memory \
		pmezard:go-difflib:v1.0.0:pmezard_go_difflib/vendor/github.com/pmezard/go-difflib \
		rivo:tview:2e69b7385a37:rivo_tview/vendor/github.com/rivo/tview \
		rivo:uniseg:v0.4.2:rivo_uniseg/vendor/github.com/rivo/uniseg \
		sirupsen:logrus:v1.9.0:sirupsen_logrus/vendor/github.com/sirupsen/logrus \
		spf13:cobra:v1.5.0:spf13_cobra/vendor/github.com/spf13/cobra \
		spf13:pflag:v1.0.5:spf13_pflag/vendor/github.com/spf13/pflag \
		stretchr:testify:v1.8.0:stretchr_testify/vendor/github.com/stretchr/testify

_BUILD_VERSION=	${DISTVERSIONFULL}
_BUILD_MAJOR=	${_BUILD_VERSION:C/\..*$//}
_BUILD_DATE=	$$(date +%Y-%m-%d)

GO_TARGET=	./cmd/${PORTNAME}
GO_BUILDFLAGS=	-ldflags "\
                -s -w \
		-X github.com/${GH_ACCOUNT}/${GH_PROJECT}/${_BUILD_MAJOR}/build.Version=${_BUILD_VERSION} \
		-X github.com/${GH_ACCOUNT}/${GH_PROJECT}/${_BUILD_MAJOR}/build.Time=${_BUILD_DATE}"

CONFLICTS_INSTALL=	coreutils

PLIST_FILES=	bin/${PORTNAME}
PORTDOCS=	README.md

OPTIONS_DEFINE=		DOCS MANPAGES
OPTIONS_DEFAULT=	MANPAGES

MANPAGES_PLIST_FILES=	man/man1/${PORTNAME}.1.gz

post-install-DOCS-on:
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/${PORTDOCS} \
		${STAGEDIR}${DOCSDIR}

post-install-MANPAGES-on:
	${INSTALL_MAN} ${WRKSRC}/${PORTNAME}.1 \
		${STAGEDIR}${MAN1PREFIX}/man/man1

.include <bsd.port.mk>
