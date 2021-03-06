# Created by: Yuri Victorovich <yuri@rawbw.com>
# $FreeBSD$

PORTNAME=	opendht
DISTVERSION=	1.6.1
CATEGORIES=	devel net

MAINTAINER=	yuri@FreeBSD.org
COMMENT=	Lightweight Distributed Hash Table implementation

LICENSE=	GPLv3
LICENSE_FILE=	${WRKSRC}/COPYING

LIB_DEPENDS=	libargon2.so:security/libargon2 \
		libmsgpackc.so:devel/msgpack \
		libnettle.so:security/nettle \
		libgnutls.so:security/gnutls

USES=		cmake:outsource compiler:c++11-lib pathfix pkgconfig readline:port
USE_GITHUB=	yes
GH_ACCOUNT=	savoirfairelinux
USE_LDCONFIG=	yes

CMAKE_OFF=	OPENDHT_STATIC

OPTIONS_DEFINE=	PROXY_SERVER PROXY_CLIENT PUSH_NOTIFICATIONS DOCS

PROXY_SERVER_DESC=		Enable DHT proxy server
PROXY_CLIENT_DESC=		Enable DHT proxy client
PUSH_NOTIFICATIONS_DESC=	Enable push notifications support

PROXY_SERVER_CMAKE_BOOL=	OPENDHT_PROXY_SERVER
PROXY_CLIENT_CMAKE_BOOL=	OPENDHT_PROXY_CLIENT
PUSH_NOTIFICATIONS_CMAKE_BOOL=	OPENDHT_PUSH_NOTIFICATIONS

PROXY_SERVER_LIB_DEPENDS=	libjsoncpp.so:devel/jsoncpp \
				librestbed.so:www/restbed

PORTDOCS=	*

.include <bsd.port.options.mk>

.if ${OPSYS} == FreeBSD && ${OSVERSION} < 1003506
BROKEN=		no __cxa_thread_atexit() support in FreeBSD libc < 10.4
.endif

.include <bsd.port.mk>
