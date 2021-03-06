# $FreeBSD$

PORTNAME=	nextcloud
DISTVERSION=	13.0.0
CATEGORIES=	www
MASTER_SITES=	https://download.nextcloud.com/server/prereleases/

MAINTAINER=	loic.blot@unix-experience.fr
COMMENT=	Personal cloud which runs on your own server

LICENSE=	AGPLv3

USES=		cpe gettext-runtime php:web tar:bzip2 ssl
USE_PHP=	bz2 ctype curl dom fileinfo filter gd hash iconv json \
		mbstring pdo posix session simplexml xml xmlreader xmlwriter \
		xsl wddx zip zlib

NEXTCLOUD_USERNAME?=	${WWWOWN}
NEXTCLOUD_GROUPNAME?=	${WWWGRP}

WRKSRC=		${WRKDIR}/${PORTNAME}
NO_BUILD=	yes
NO_ARCH=	yes
SUB_FILES=	pkg-message
PLIST_SUB=	NEXTCLOUD_USERNAME=${NEXTCLOUD_USERNAME} \
		NEXTCLOUD_GROUPNAME=${NEXTCLOUD_GROUPNAME}

OPTIONS_DEFINE=	EXIF LDAP SMB SSL
OPTIONS_MULTI=	DB
OPTIONS_MULTI_DB=	MYSQL PGSQL SQLITE
OPTIONS_DEFAULT=	EXIF LDAP MYSQL SMB SSL

DB_DESC=	Database backend(s)
EXIF_DESC=	Image rotation support

EXIF_USE=	PHP=exif
LDAP_USE=	PHP=ldap
MYSQL_USES=	mysql
MYSQL_USE=	PHP=pdo_mysql
PGSQL_USES=	pgsql
PGSQL_USE=	PHP=pdo_pgsql,pgsql
SQLITE_USE=	PHP=pdo_sqlite,sqlite3
SMB_RUN_DEPENDS=	${PECL_PKGNAMEPREFIX}smbclient>=0.8.0:net/pecl-smbclient@${PHP_FLAVOR}
SSL_USE=	PHP=openssl

post-patch:
	@${REINPLACE_CMD} -e 's|/var/www/|${WWWDIR}|' ${WRKSRC}/config/config.sample.php

do-install:
	@${MKDIR} -m 0755 ${STAGEDIR}${WWWDIR}
	@cd ${WRKSRC} && ${COPYTREE_SHARE} . ${STAGEDIR}${WWWDIR}
	@${RM} ${STAGEDIR}${WWWDIR}/updater/updater.phar
	@${MKDIR} ${STAGEDIR}${WWWDIR}/data

.include <bsd.port.mk>
