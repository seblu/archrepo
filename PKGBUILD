# Maintainer: Sébastien Luttringer

pkgname=archrepo-git
pkgver=$(git log --pretty=format:''|wc -l)
#pkgver=$(date +%Y.%m.%d)
pkgrel=1
pkgdesc='Seblu Archlinux Repositories Stuff'
arch=('any')
url='https://github.com/seblu/archrepo'
license=('GPL2')
makedepends=('git')
depends=('bash' 'devtools' 'hardlink')

package() {
  cd "$startdir"
  install -dm755 "$pkgdir"/usr/{share/licenses/$pkgname,share/devtools,bin}
  # install legal stuff
  install -m644 COPYRIGHT LICENSE "$pkgdir/usr/share/licenses/$pkgname"
  # install config
  install -m644 pacman-seblu.conf "$pkgdir/usr/share/devtools"
  install -m644 pacman-multilib-seblu.conf "$pkgdir/usr/share/devtools"
  # install binaries
  install -m755 seblu-build seblu-build-commit seblu-mirrors seblu-commit \
    seblu-remove seblu-cleanup seblu-push update-arch-chroots \
    "$pkgdir/usr/bin"
  # symlink archbuild
  ln -s archbuild "$pkgdir/usr/bin/seblu-x86_64-build"
  ln -s archbuild "$pkgdir/usr/bin/multilib-seblu-build"
  # symlink to seblu-build
  ln -s seblu-build "$pkgdir/usr/bin/extra-build"
  ln -s seblu-build "$pkgdir/usr/bin/testing-build"
  ln -s seblu-build "$pkgdir/usr/bin/staging-build"
  # add sudo config
  install -dm750 "$pkgdir/etc/sudoers.d"
  install -m644 sudoers "$pkgdir/etc/sudoers.d/50-devtools-seblu"
}

# vim:set ts=2 sw=2 et:
