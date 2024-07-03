# Maintainer: Ashley Bone <ashley DOT bone AT pm DOT me>
# Contributor: Carlos Aznarán <caznaranl@uni.pe>
pkgname=('python-portalocker')
_pkgname=portalocker
pkgver=2.10.0
pkgrel=1
pkgdesc='Easy, portable file locking API.'
arch=('any')
url="https://github.com/WoLpH/portalocker"
license=('PSF')
depends=('python')
makedepends=('python-build' 'python-installer' 'python-pygments' 'python-setuptools' 'python-setuptools-scm' 'python-wheel')
checkdepends=('python-pytest' 'python-pytest-cov' 'python-pytest-timeout' 'python-redis')
optdepends=('python-redis: redis lock support')
source=("${_pkgname}-${pkgver}::https://github.com/wolph/portalocker/archive/refs/tags/v${pkgver}.tar.gz")
sha256sums=('d4d4418bf730bc19d0a4b0a0201cb3b004c59b1e1770fa3f5c4a139e0d524802')

build() {
    cd "${srcdir}/${_pkgname}-${pkgver}"
    python -m build --wheel --no-isolation
}

check() {
    cd "${srcdir}/${_pkgname}-${pkgver}"
    pytest
}

package() {
    cd "${srcdir}/${_pkgname}-${pkgver}"
    python -m installer --destdir="${pkgdir}" dist/*.whl
    install -Dm 644 LICENSE -t "${pkgdir}/usr/share/licenses/${pkgname}"
}
