#!/bin/bash

# Based on the original PKGBUILD by Zepman <the_zep_man@hotmail.com>, Christian Hesse <mail@eworm.de>, Constantinko <helllamer@gmail.com> and Agustín Dall'Alba <a@dallalba.com.ar>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors

# Maintainer: Ross Clark <https://github.com/Archiv8/httpfs2-2gbplus/discussions>
# Contributor: Ross Clark <https://github.com/Archiv8/httpfs2-2gbplus/discussions>

_relname="-2gbplus"

pkgname="${_relname}"
pkgver=0.1.5
pkgrel=1
pkgdesc="FUSE-based file system for HTTP access, patched with +2GB file support"
arch=(
  "i686"
  "x86_64")
url="http://httpfs.sourceforge.net/"
license=(
  "GPL"
)
depends=(
  "fuse"
  "openssl"
)
makedepends=(
  "asciidoc"
  "dpkg"
)
provides=(
  "httpfs2"
)
conflicts=(
  "httpfs2"
)
source=(
  "http://downloads.sourceforge.net/project/httpfs/httpfs2/${_relname}-${pkgver}.tar.gz"
  "https://sourceforge.net/p/httpfs/bugs/_discuss/thread/8a4f3458/b43f/attachment/httpfs.diff"
)
sha512sums=(
  "01cb4bb38deb344f540da6f1464dc7edbdeb51213ad810b8c9c282c1e17e0fc1"
  "da1965ff43662ed1473699e94511d9ae1c493d071eee795cdb5ff22fabeebc56"
)

prepare() {
  cd "${srcdir}"/${_relname}-${pkgver}
  patch -p1 -i ../httpfs.diff
}

build() {
  cd "${srcdir}"/${_relname}-${pkgver}

  make
}

package() {
  cd "${srcdir}"/${_relname}-${pkgver}

  install -D -m0755 httpfs2 "${pkgdir}"/usr/bin/httpfs2
  install -D -m0755 httpfs2-ssl "${pkgdir}"/usr/bin/httpfs2-ssl

  install -D -m0644 httpfs2.1 "${pkgdir}"/usr/share/man/man1/httpfs2.1

  install -D -m0644 debian/copyright "${pkgdir}"/usr/share/doc/httpfs2/copyright
}
