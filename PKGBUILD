# Original author sputnick <gilles *DOT* quenot *AT* gmail *DOT* com>
# Maintener Julien Pecqueur (JPEC) <jpec@julienpecqueur.net>

pkgname=weboob-nox-git
pkgrel=1
pkgver=20130401
pkgdesc="Weboob (Web Out Of Browsers) provides several applications to interact with a lot of websites. NO X VERSION."
url="http://weboob.org"
license=('GPL3')
arch=('i686' 'x86_64' 'armv6h')
depends=('python2' 'python2-dateutil' 'python2-cssselect' 'python2-mechanize' 'python2-elementtidy' 'python2-html2text' 'python2-yaml' 'python2-lxml' 'python2-html5lib' 'python2-feedparser' 'python2-gdata' 'python2-prettytable' 'python2-pysqlite' 'python2-simplejson' 'mimms')
makedepends=('git' 'setuptools')
optdepends=(
    'gnupg: check for repository authenticity'
    'python2-routes: contrib backends'
    'python2-webob: contrib backends'
    'python2-mako: contrib backends'
    'python2-nose: test suite'
)
conflicts=('weboob' 'weboob-git')
provides=('weboob')

_gitroot="git://git.symlink.me/pub/romain/weboob.git"
_gitname=weboob

build() {
	cd $srcdir
	msg "Connecting to GIT server...."

	if [[ -d $srcdir/$_gitname ]]; then
		cd $_gitname && git pull origin
		msg "The local files are updated."
		cd ../
	else
		git clone $_gitroot
	fi

	msg "GIT checkout done or server timeout"

	rm -rf build
	git clone $_gitname build
	cd build

	python2 setup.py install --no-qt --no-xdg --root=$pkgdir
} 
