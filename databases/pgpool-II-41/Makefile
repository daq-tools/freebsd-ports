PORTNAME=	pgpool-II
PORTVERSION=	4.1.15
CATEGORIES=	databases
MASTER_SITES=	http://www.pgpool.net/mediawiki/images/
PKGNAMESUFFIX=	41

MAINTAINER=	tz@FreeBSD.org
COMMENT=	Connection pool server for PostgreSQL
WWW=		https://pgpool.net/

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/COPYING

USES=		gmake libtool pgsql:11+
USE_LDCONFIG=	yes
USE_RC_SUBR=	pgpool

GNU_CONFIGURE=	yes

CONFLICTS_INSTALL=	pgpool-II-[0-9][0-9] pgpool-II[0-9][0-9] # etc/failover.sh.sample etc/pcp.conf.sample

PORTSCOUT=	limit:^4.1.[0-9]*

PORTDOCS=	*

OPTIONS_DEFINE=		DOCS MEMCACHED PAM SSL
OPTIONS_DEFAULT=	SSL

MEMCACHED_DESC=	Use memcached for in memory query cache
PAM_DESC=	Build with PAM support
SSL_DESC=	Build with OpenSSL support

MEMCACHED_LIB_DEPENDS=	libmemcached.so:databases/libmemcached
MEMCACHED_CONFIGURE_ON=	--with-memcached=${LOCALBASE}/include
PAM_CONFIGURE_ON=	--with-pam
SSL_USES=		ssl
SSL_CONFIGURE_WITH=	openssl

.include <bsd.port.options.mk>

.if ${OPSYS} == FreeBSD && ${OSVERSION} >= 1400079
CFLAGS+=	-Wno-error=int-conversion
.endif

post-install:
	@${MKDIR} ${STAGEDIR}/var/run/pgpool
	${INSTALL_LIB} ${WRKSRC}/src/libs/pcp/.libs/libpcp.so.1.0.0 ${STAGEDIR}${PREFIX}/lib

post-install-DOCS-on:
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	cd ${WRKSRC} && ${COPYTREE_SHARE} doc ${STAGEDIR}${DOCSDIR} "-not -name Makefile.\*"
.for f in AUTHORS ChangeLog NEWS TODO
	${INSTALL_DATA} ${WRKSRC}/$f ${STAGEDIR}${DOCSDIR}
.endfor

.include <bsd.port.mk>
