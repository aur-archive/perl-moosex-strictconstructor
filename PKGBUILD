# Maintainer: Maxwell Pray a.k.a. Synthead <synthead@gmail.com>

pkgname=perl-moosex-strictconstructor
_cpanname="MooseX-StrictConstructor"
pkgver=0.19
pkgrel=1
pkgdesc="Make your object constructors blow up on unknown attributes"
arch=('any')
url="http://search.cpan.org/~drolsky/$_cpanname"
license=('GPL' 'PerlArtistic')
depends=('perl>=5.5.0' 'perl-namespace-autoclean')
options=('!emptydirs')
source=("http://search.cpan.org/CPAN/authors/id/D/DR/DROLSKY/$_cpanname-$pkgver.tar.gz")
md5sums=('66cd34ce309c16e2cfe44ba626916bbb')

# Function to change to the working directory and set
# environment variables to override undesired options.
prepareEnvironment() {
	cd "$srcdir/$_cpanname-$pkgver"
	export \
		PERL_MM_USE_DEFAULT=1 \
		PERL_AUTOINSTALL=--skipdeps \
		PERL_MM_OPT="INSTALLDIRS=vendor DESTDIR='$pkgdir'" \
		PERL_MB_OPT="--installdirs vendor --destdir '$pkgdir'" \
		MODULEBUILDRC=/dev/null
}

build() {
	prepareEnvironment
	/usr/bin/perl Makefile.PL
	make
}

check() {
	prepareEnvironment
	make test
}

package() {
	prepareEnvironment
	make install

	# Remove "perllocal.pod" and ".packlist".
	find "$pkgdir" -name .packlist -o -name perllocal.pod -delete
}
