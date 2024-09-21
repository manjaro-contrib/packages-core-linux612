# Maintainer: Bernhard Landauer <bernhard@manjaro.org>
# Maintainer: Philip Müller <philm[at]manjaro[dot]org>
# Archlinux maintainers:
# Tobias Powalowski <tpowa@archlinux.org>
# Thomas Baechler <thomas@archlinux.org>

_basekernel=6.12
_basever=${_basekernel//.}
_kernelname=-MANJARO
_commit=1868f9d0260e9afaf7c6436d14923ae12eaea465
_rc=rc0
pkgbase=linux${_basever}
pkgname=("$pkgbase" "$pkgbase-headers")
pkgver=6.12.0rc0
pkgrel=1
arch=('x86_64')
url="https://www.kernel.org/"
license=('GPL2')
makedepends=(bc docbook-xsl libelf pahole python-sphinx git inetutils kmod xmlto cpio perl tar xz rust rust-bindgen rust-src)
options=('!strip')
source=(#"https://www.kernel.org/pub/linux/kernel/v6.x/linux-${_basekernel}.tar.xz"
        #https://github.com/torvalds/linux/archive/refs/tags/v${_basekernel}-${_rc}.tar.gz
        https://github.com/torvalds/linux/archive/${_commit}.tar.gz
        #https://www.kernel.org/pub/linux/kernel/v6.x/patch-${pkgver}.xz
        config
        # Upstream Patches
        # ARCH Patches
        0101-ZEN_Add_sysctl_and_CONFIG_to_disallow_unprivileged_CLONE_NEWUSER.patch
        0102-drivers-firmware-skip-simpledrm-if-nvidia-drm.modese.patch
        0103_default_to_max_ASLR_bits.patch
        # Realtek patch
        0999-patch_realtek.patch
        # IIO patches
        0001-iio-trigger-allow-devices-to-suspend-resume-theirs-a.patch
        0002-iio-bmi323-suspend-and-resume-triggering-on-relevant.patch
        0003-iio-bmi323-peripheral-in-lowest-power-state-on-suspe.patch
        # ROG ALLY Patches (stable)
        0004-Input-xpad-add-support-for-ASUS-ROG-RAIKIRI-PRO.patch
        0007-acpi-x86-s2idle-add-support-for-screen-off-and-scree.patch
        0008-drm-Notify-the-suspend-core-when-displays-are-change.patch
        0009-acpi-x86-s2idle-Move-screen-off-on-code-into-dedicat.patch
        0010-platform-x86-asus-wmi-Refactor-Ally-suspend-resume.patch
        0011-platform-x86-asus-armoury-move-existing-tunings-to-a.patch
        0012-platform-x86-asus-armoury-add-dgpu-tgp-control.patch
        0013-platform-x86-asus-armoury-add-apu-mem-control-suppor.patch
        0014-platform-x86-asus-armoury-add-core-count-control.patch
        0015-platform-x86-asus-wmi-deprecate-bios-features.patch
        0016-hid-asus-ally-Add-full-gamepad-support.patch
        # OrangePi Neo patches
        0001-iio_imu_Add_driver_for_Bosch_BMI260_IMU.patch
        # Steamdeck (OLED)
        0001-steam-deck.patch
        0002-steamdeck-oled-audio.patch
)

if [[ ! -z "$_commit" ]]; then
  _srcdir="linux-${_commit}"
elif [[ ! -z "$_rc" ]]; then
  _srcdir="linux-${_basekernel}-${_rc}"
else
  _srcdir="linux-${_basekernel}"
fi

sha256sums=('69b628e0d899a6b9ba3613e3751f0f889f2841bad1ac904c5502d4827c350788'
            'f4808cb1e1d053fb456400c27bedad48b7bb037e641b0c42f0dee99e592351fa'
            '888a89ec67433ddfd71ba187a7356ca60270dbe51d6df7211e3930f13121ba8c'
            '934bc233684c45860251bb75433d671b23fa784c891ab3a1ef10d5bc761156b6'
            '6400a06e6eb3a24b650bc3b1bba9626622f132697987f718e7ed6a5b8c0317bc'
            'b88d42565ce771cb6c8f98b7c05aada6b8024578a1985e5772dc5a2d07facee0'
            '02d617ae99e6a6a159dfc7299308c765fb66764148c2c549d40191646c5e2dd4'
            '65b7b008b392693974a319a8a1ab5c1a3492474faf3cb7c45d94a1f4811e0820'
            'd99d7db369b7c4f31b21002914ba1135ecf344b3fb30a01be7d444ead43dd9f9'
            'f22d038b3ff02bfbcc7ecc81fea434ff669f702cc6681dc41f292c0048e28f19'
            'cd0a28c004c0a74f77d27a2469013695e75f5b69c50f1fb619ad8db24a292f5f'
            'bb06dd497cff0450f966c2cb30c28213b49059b9bfb4e847265ebe5075dacd2e'
            '5051e0988fed9f1e9bccf68448abed960759932fed12f9c6259667b81ca7ab22'
            '5684a9539b93218d389afbb5c0f8dc75299d4c35605890cc96e50a184102e7c1'
            '98f052fb99ffc06effe72456151b5e98e0780df718429def3dd9d0fb7d116475'
            '9bb04bd737c5c7bfc48bef16d99a52e1ba0d8088fcddd723b210f2f7be1282fe'
            '00882a0a21e4f983c73fa4bf7852857cda587f1e66a42ba80f0cc5c30645d847'
            'ef98d9148badf4b6e43934ac6b4ebc1987956ac2d01db3609fd1a63f42f09a79'
            '6885539a78271001cd1cd032646287c7c50b1a65a6bef50791fae8832cef10ea'
            'c3360c0c62ad02d9ee92edafe1b2c8e928e0f4ff0100fb3e900171a4dd3aec54'
            'e58b6631da6dcc302984c30882276026a449228833cfb01d157a85ff1064080e'
            'f8cf8ad3e17857b51c3f7dd954eb5ac7ba44bfe0302a40e70b2c496573407edf'
            '17c49b6eb2602d4796b8c47e8e9c30684404f9300d71278475ddf61a4025ca88')

prepare() {
  cd "$_srcdir"

  # add upstream patch
  if [[ -z "$_rc" ]] && [[ -e "../patch-${pkgver}" ]]; then
    msg "add upstream patch"
    patch -p1 -i "../patch-${pkgver}"
  fi

  local src
  for src in "${source[@]}"; do
      src="${src%%::*}"
      src="${src##*/}"
      [[ $src = *.patch ]] || continue
      msg2 "Applying patch: $src..."
      patch -Np1 < "../$src"
  done

  msg2 "add config"
  cat "../config" > ./.config

  if [ "${_kernelname}" != "" ]; then
    sed -i "s|CONFIG_LOCALVERSION=.*|CONFIG_LOCALVERSION=\"${_kernelname}\"|g" ./.config
    sed -i "s|CONFIG_LOCALVERSION_AUTO=.*|CONFIG_LOCALVERSION_AUTO=n|" ./.config
  fi

  msg "set extraversion to pkgrel"
  [[ "$_rc" ]] && sed -ri "s|^(EXTRAVERSION =).*|\1 -${_rc}-${pkgrel}|" Makefile
  [[ -z "$_rc" ]] && sed -ri "s|^(EXTRAVERSION =).*|\1 -${pkgrel}|" Makefile

  msg "set patchlevel to 12"
  sed -ri "s|PATCHLEVEL = 11|PATCHLEVEL = 12|" Makefile

  msg "don't run depmod on 'make install'"
  # We'll do this ourselves in packaging
  sed -i '2iexit 0' scripts/depmod.sh

  msg "get kernel version"
  make prepare

  msg "rewrite configuration"
  yes "" | make config # >/dev/null
}

build() {
  cd "$_srcdir"

  msg "build"
  make ${MAKEFLAGS} LOCALVERSION= bzImage modules
}

package_linux612() {
  pkgdesc="The ${pkgbase/linux/Linux} kernel and modules"
  depends=('coreutils' 'linux-firmware' 'kmod' 'initramfs')
  optdepends=('wireless-regdb: to set the correct wireless channels of your country')
  provides=("linux=${pkgver}" VIRTUALBOX-GUEST-MODULES WIREGUARD-MODULE KSMBD-MODULE)

  cd "$_srcdir"

  # get kernel version
  _kernver="$(make LOCALVERSION= kernelrelease)"

  mkdir -p "${pkgdir}"/{boot,usr/lib/modules}
  ZSTD_CLEVEL=19 make LOCALVERSION= INSTALL_MOD_PATH="${pkgdir}/usr" \
  INSTALL_MOD_STRIP=1 modules_install

  # systemd expects to find the kernel here to allow hibernation
  # https://github.com/systemd/systemd/commit/edda44605f06a41fb86b7ab8128dcf99161d2344
  cp arch/x86/boot/bzImage "${pkgdir}/usr/lib/modules/${_kernver}/vmlinuz"

  # Used by mkinitcpio to name the kernel
  echo "${pkgbase}" | install -Dm644 /dev/stdin "${pkgdir}/usr/lib/modules/${_kernver}/pkgbase"
  echo "${_basekernel}-${CARCH}" | install -Dm644 /dev/stdin "${pkgdir}/usr/lib/modules/${_kernver}/kernelbase"

  # add kernel version
  echo "${pkgver}-${pkgrel}-MANJARO x64" > "${pkgdir}/boot/${pkgbase}-${CARCH}.kver"

  # remove build and source links
  rm "${pkgdir}"/usr/lib/modules/${_kernver}/build

  # now we call depmod...
  depmod -b "${pkgdir}/usr" -F System.map "${_kernver}"
}

package_linux612-headers() {
  pkgdesc="Header files and scripts for building modules for ${pkgbase/linux/Linux} kernel"
  depends=('gawk' 'python' 'libelf' 'pahole')
  provides=("linux-headers=$pkgver")

  cd "$_srcdir"
  local _builddir="${pkgdir}/usr/lib/modules/${_kernver}/build"

  # add real version for building modules and running depmod from hook
  echo "${_kernver}" |
    install -Dm644 /dev/stdin "${_builddir}/version"

  install -Dt "${_builddir}" -m644 Makefile .config Module.symvers
  install -Dt "${_builddir}/kernel" -m644 kernel/Makefile
  install -Dt "${_builddir}" -m644 vmlinux

  mkdir "${_builddir}/.tmp_versions"

  cp -t "${_builddir}" -a include scripts

  install -Dt "${_builddir}/arch/x86" -m644 "arch/x86/Makefile"
  install -Dt "${_builddir}/arch/x86/kernel" -m644 "arch/x86/kernel/asm-offsets.s"

  cp -t "${_builddir}/arch/x86" -a "arch/x86/include"

  install -Dt "${_builddir}/drivers/md" -m644 drivers/md/*.h
  install -Dt "${_builddir}/net/mac80211" -m644 net/mac80211/*.h

  # https://bugs.archlinux.org/task/13146
  install -Dt "${_builddir}/drivers/media/i2c" -m644 drivers/media/i2c/msp3400-driver.h

  # https://bugs.archlinux.org/task/20402
  install -Dt "${_builddir}/drivers/media/usb/dvb-usb" -m644 drivers/media/usb/dvb-usb/*.h
  install -Dt "${_builddir}/drivers/media/dvb-frontends" -m644 drivers/media/dvb-frontends/*.h
  install -Dt "${_builddir}/drivers/media/tuners" -m644 drivers/media/tuners/*.h

  # https://bugs.archlinux.org/task/71392
  install -Dt "${_builddir}/drivers/iio/common/hid-sensors" -m644 drivers/iio/common/hid-sensors/*.h

  # add xfs and shmem for aufs building
  mkdir -p "${_builddir}"/{fs/xfs,mm}

  # copy in Kconfig files
  find . -name Kconfig\* -exec install -Dm644 {} "${_builddir}/{}" \;

  # add objtool for external module building and enabled VALIDATION_STACK option
  install -Dt "${_builddir}/tools/objtool" tools/objtool/objtool

  # https://forum.manjaro.org/t/90629/39
  install -Dt "${_builddir}/tools/bpf/resolve_btfids" tools/bpf/resolve_btfids/resolve_btfids

  # remove unneeded architectures
  local _arch
  for _arch in "${_builddir}"/arch/*/; do
    [[ ${_arch} == */x86/ ]] && continue
    rm -r "${_arch}"
  done

  # remove documentation files
  rm -r "${_builddir}/Documentation"

  # strip scripts directory
  local file
  while read -rd '' file; do
    case "$(file -bi "$file")" in
      application/x-sharedlib\;*)      # Libraries (.so)
        strip $STRIP_SHARED "$file" ;;
      application/x-archive\;*)        # Libraries (.a)
        strip $STRIP_STATIC "$file" ;;
      application/x-executable\;*)     # Binaries
        strip $STRIP_BINARIES "$file" ;;
      application/x-pie-executable\;*) # Relocatable binaries
        strip $STRIP_SHARED "$file" ;;
    esac
  done < <(find "${_builddir}" -type f -perm -u+x ! -name vmlinux -print0 2>/dev/null)
  strip $STRIP_STATIC "${_builddir}/vmlinux"

  echo "Adding symlink..."
  mkdir -p "${pkgdir}/usr/src"
  ln -sr "${_builddir}" "${pkgdir}/usr/src/${pkgbase}"

  # remove unwanted files
  find ${_builddir} -name '*.orig' -delete
}
