# Maintaier: Martin Filion < mordillo98@gmail.com >

pkgname=afetch
pkgver=2.2.0
pkgrel=1
pkgdesc="A fetch program written in C"
arch=('x86_64')
url="https://github.com/13-CF/afetch"
license=('GPL3')
source=("git+https://github.com/13-CF/afetch.git")
md5sums=('SKIP')

build() {
	cd "$pkgname"
        
        patch src/config.h < ../../config.patch                 
        patch src/fetch.c < ../../fetch.patch 
	
        echo ":: If $pkgname fails to compile, check that you have a libc installed with pthread support."
	make CFLAGS="${CFLAGS} -std=c99" LDFLAGS="${LDFLAGS} -lpthread" all
}

package() {
	cd "$pkgname"
	install -Dm 755 "$pkgname" -t "$pkgdir/usr/bin/"
	install -Dm 644 README.md -t "$pkgdir/usr/share/doc/$pkgname/"
}
