# Created by: Gustau Perez i Querol <gustau.perez@gmail.com>
# $FreeBSD$

PORTNAME=	gnome-shell-extension-mediaplayer
PORTVERSION=	0.0.0.20151118
CATEGORIES=	deskutils gnome
DIST_SUBDIR=	gnome3

MAINTAINER=	gnome@FreeBSD.org
COMMENT=	MPRIS2 extension for the GNOME3 shell

BUILD_DEPENDS=	gnome-autogen.sh:devel/gnome-common \
		gsettings-desktop-schemas>=3.12.0:devel/gsettings-desktop-schemas
RUN_DEPENDS=	gnome-shell>=0:x11/gnome-shell \
		gsettings-desktop-schemas>=3.12.0:devel/gsettings-desktop-schemas

USES=		autoreconf gettext gmake gnome libtool pkgconfig
USE_GNOME=	glib20 intltool
USE_GITHUB=	yes
USE_LDCONFIG=	yes
GNU_CONFIGURE=	yes
CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib
GLIB_SCHEMAS=	org.gnome.shell.extensions.mediaplayer.gschema.xml

GH_ACCOUNT=	eonpatapon
GH_PROJECT=	gnome-shell-extensions-mediaplayer
GH_TAGNAME=	ffabc47

PKGMESSAGE=	../gnome-shell-extra-extensions/pkg-message.slaves

.include <bsd.port.mk>
