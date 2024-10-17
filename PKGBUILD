# Maintainer: Bernhard Landauer <bernhard@manjaro.org>
# Maintainer: Philip Müller <philm[at]manjaro[dot]org>
# Archlinux maintainers:
# Tobias Powalowski <tpowa@archlinux.org>
# Thomas Baechler <thomas@archlinux.org>

_basekernel=6.12
_basever=${_basekernel//.}
_kernelname=-MANJARO
_commit=
_rc=rc3
pkgbase=linux${_basever}
pkgver=6.12.0rc3
pkgrel=3
arch=('x86_64')
url="https://www.kernel.org/"
license=(GPL-2.0-only)
makedepends=(
  bc
  cpio
  gettext
  libelf
  pahole
  perl
  python
  tar
  xz
)
options=(
  !debug
  !strip
)
source=(#"https://www.kernel.org/pub/linux/kernel/v6.x/linux-${_basekernel}.tar.xz"
        https://github.com/torvalds/linux/archive/refs/tags/v${_basekernel}-${_rc}.tar.gz
        #https://github.com/torvalds/linux/archive/${_commit}.tar.gz
        #https://www.kernel.org/pub/linux/kernel/v6.x/patch-${pkgver}.xz
        config
        # Upstream Patches
        # ARCH Patches
        0101-ZEN_Add_sysctl_and_CONFIG_to_disallow_unprivileged_CLONE_NEWUSER.patch
        0102-drivers-firmware-skip-simpledrm-if-nvidia-drm.modese.patch
        0103_default_to_max_ASLR_bits.patch
        # Realtek patch
        0999-patch_realtek.patch
        # ROG ALLY Patches (stable)
        #0001-Fix-ROG-ALLY-X-audio.patch
        #0002-platform-x86-asus-wmi-add-support-for-vivobook-fan-p.patch
        #0003-hid-asus-use-hid-for-brightness-control-on-keyboard.patch
        0004-Input-xpad-add-support-for-ASUS-ROG-RAIKIRI-PRO.patch
        #0005-platform-x86-asus-wmi-add-debug-print-in-more-key-pl.patch
        #0006-platform-x86-asus-wmi-don-t-fail-if-platform_profile.patch
        0007-Revert-platform-x86-asus-wmi-ROG-Ally-increase-wait-.patch
        0008-Revert-platform-x86-asus-wmi-disable-USB0-hub-on-ROG.patch
        0009-platfom-x86-asus-wmi-cleanup-after-reverts.patch
        0010-platform-x86-asus-wmi-export-symbols-used-for-read-w.patch
        0011-hid-asus-Add-MODULE_IMPORT_NS-ASUS_WMI.patch
        0012-platform-x86-asus-armoury-move-existing-tunings-to-a.patch
        0013-platform-x86-asus-armoury-add-panel_hd_mode-attribut.patch
        0014-platform-x86-asus-armoury-add-the-ppt_-and-nv_-tunin.patch
        0015-platform-x86-asus-armoury-add-dgpu-tgp-control.patch
        0016-platform-x86-asus-armoury-add-apu-mem-control-suppor.patch
        0017-platform-x86-asus-armoury-add-core-count-control.patch
        0018-platform-x86-asus-wmi-deprecate-bios-features.patch
        #0019-ACPI-PM-Quirk-ASUS-ROG-M16-to-default-to-S3-sleep.patch
        #0020-ACPI-CPPC-Add-support-for-setting-EPP-register-in-FF.patch
        0021-hid-asus-ally-Add-joystick-LED-ring-support.patch
        0022-hid-asus-ally-initial-Ally-X-gamepad.patch
        0023-hid-asus-ally-initial-gamepad-configuration.patch
        0024-hid-asus-ally-add-button-remap-attributes.patch
        0025-hid-asus-ally-Turbo-settings-for-buttons.patch
        0026-hid-asus-ally-add-gamepad-modes-and-defaults.patch
        0027-hid-asus-ally-add-vibration-intensity-settings.patch
        0028-hid-asus-ally-add-JS-deadzones.patch
        0029-hid-asus-ally-add-trigger-deadzones.patch
        0030-hid-asus-ally-add-anti-deadzones.patch
        0031-hid-asus-ally-add-JS-response-curves.patch
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

sha256sums=('c9b271cc559588796a80f06f4198a4de2823bc28cb5cd2632f3b80401035b91d'
            'b87e3fbd3ae73f6b51981cea30505ef4c9c33d24bc6995244f12d8cab1d8f5bd'
            '888a89ec67433ddfd71ba187a7356ca60270dbe51d6df7211e3930f13121ba8c'
            '934bc233684c45860251bb75433d671b23fa784c891ab3a1ef10d5bc761156b6'
            '6400a06e6eb3a24b650bc3b1bba9626622f132697987f718e7ed6a5b8c0317bc'
            'b88d42565ce771cb6c8f98b7c05aada6b8024578a1985e5772dc5a2d07facee0'
            '1c3df472dfee1457f40cf5ee5d72e1b5de30df6cb6f0515b177b8736244a351d'
            'a9a8114a9c98dcc85f0b7cf59588ecc64be4f7b85cc75743c22fbbe1000bb326'
            'cada1756b79efd67cacdf410d2f9ca30182760209e99878c2a72e488bb627073'
            '725e005d0231495016be223405998c9d9fc320632394e3ad51e723aa5782195d'
            '46dbaa87136178f0ed6bbc637cf33161b29847fbd60197fb2710c7e31cfe2ed5'
            'e859bd064931121df97163ec5ff895ed78025ad6a3ed9c5fb56615f990e85499'
            '89ea82c8f03f004b2ad63d980b6d272c2af81e2bbb7189fd76b0749e05c77c32'
            '50de31b906969eacabd98acb44672376fffb1c20f350990e2f3432d0863f2f19'
            '270ba87d47f88c6d4f1d6f0207667a6b7ef2430d5afd7ce69b94dac50a5407fd'
            'd8416b8e79e1f9e37de0f1ae9bcba8ede1ce7c07a889624d90746d876853e906'
            '613d2f20e6dabf4eb44080013f591f57621cf2e15aeef04f1c008231e5475268'
            'edd01df4c26a9660e487225a4830897f955cd145f62e536a4958621b2b197333'
            '55f9ab848d43f98cee82aefc0113fd898613fa6d6db92da62162b407fb8fcc9f'
            '5d5e68bab741b7692ce117f8f4fc869927ff61929f23a49923285831ad887400'
            '6051c43ba9195b7aedadb180e4bf7aa1d24259742d69c060cb6f57e9e9e0be1b'
            'eb396b9a3b5251a2101ff78039d128e2155d9b4bd5a907c8c8d8ec1d685730f5'
            '66b3536134aea922f458de50bdb2182b6f179dd6ff6668af8191a936220553dd'
            '5b3cd6758cac6bcebcf908bfbcfbe23de375ff3a1c214ebe4441e9f496d40fd1'
            '0b388449235cb18eb080719d13ddc4bef5308c7aa127c149fc919491df23ff33'
            'af9657d5f9c136f08e8c5e8c95a4c3d8872dbce23d4c4a31049a9beeaa369552'
            'dcb2732dc891e78d4f1dc889d4c4045368380d40dc1bca34e996adfd45ce6dae'
            '6a0423752d2578de78691bf995ced5ff84220328ee961aae38900067ccc177f1'
            '5dffc3f2cf681d9a27b40bec4361533d01ead6beca3eb33153dd434c5fca8d43'
            '0fff5fb87b42be67af6592465c8284954332baab728ce9c1326dc712e219ef86'
            'e58b6631da6dcc302984c30882276026a449228833cfb01d157a85ff1064080e'
            'f8cf8ad3e17857b51c3f7dd954eb5ac7ba44bfe0302a40e70b2c496573407edf'
            '17c49b6eb2602d4796b8c47e8e9c30684404f9300d71278475ddf61a4025ca88')

export KBUILD_BUILD_HOST=manjaro
export KBUILD_BUILD_USER=$pkgbase
export KBUILD_BUILD_TIMESTAMP="$(date -Ru${SOURCE_DATE_EPOCH:+d @$SOURCE_DATE_EPOCH})"

prepare() {
  cd $_srcdir

  echo "Setting version..."
  echo "-$pkgrel" > localversion.10-pkgrel

  # add upstream patch
  if [[ -z "$_rc" ]] && [[ -e "../patch-${pkgver}" ]]; then
    msg "add upstream patch"
    patch -p1 -i "../patch-${pkgver}"
  fi

  local src
  for src in "${source[@]}"; do
    src="${src%%::*}"
    src="${src##*/}"
    src="${src%.zst}"
    [[ $src = *.patch ]] || continue
    echo "Applying patch $src..."
    patch -Np1 < "../$src"
  done

  echo "Setting config..."
  cp ../config .config
  make olddefconfig
  diff -u ../config .config || :

  make -s kernelrelease > version
  echo "Prepared $pkgbase version $(<version)"
}

build() {
  cd $_srcdir
  make ${MAKEFLAGS} bzImage modules
  make -C tools/bpf/bpftool vmlinux.h feature-clang-bpf-co-re=1
}

_package() {
  pkgdesc="The Linux $_basekernel kernel and modules"
  depends=(
    coreutils
    initramfs
    kmod
  )
  optdepends=(
    'wireless-regdb: to set the correct wireless channels of your country'
    'linux-firmware: firmware images needed for some devices'
  )
  provides=(
    "linux=${pkgver}"
    KSMBD-MODULE
    VIRTUALBOX-GUEST-MODULES
    WIREGUARD-MODULE
  )
  replaces=(
    virtualbox-guest-modules
    wireguard
  )

  cd $_srcdir
  local modulesdir="$pkgdir/usr/lib/modules/$(<version)"

  echo "Installing boot image..."
  # systemd expects to find the kernel here to allow hibernation
  # https://github.com/systemd/systemd/commit/edda44605f06a41fb86b7ab8128dcf99161d2344
  install -Dm644 "$(make -s image_name)" "$modulesdir/vmlinuz"

  # Used by mkinitcpio to name the kernel
  echo "$pkgbase" | install -Dm644 /dev/stdin "$modulesdir/pkgbase"
  echo "${_basekernel}-${CARCH}" | install -Dm644 /dev/stdin "$modulesdir/kernelbase"

  # add kernel version
  mkdir -p "${pkgdir}/boot"
  echo "$(<version) x64" > "${pkgdir}/boot/${pkgbase}-${CARCH}.kver"

  echo "Installing modules..."
  ZSTD_CLEVEL=19 make INSTALL_MOD_PATH="$pkgdir/usr" INSTALL_MOD_STRIP=1 \
    DEPMOD=/doesnt/exist modules_install  # Suppress depmod

  # remove build link
  rm "$modulesdir"/build

  # now we call depmod...
  depmod -b "${pkgdir}/usr" -F System.map "$(<version)"
}

_package-headers() {
  pkgdesc="Headers and scripts for building modules for the Linux $_basekernel kernel"
  depends=(pahole)

  cd $_srcdir
  local builddir="$pkgdir/usr/lib/modules/$(<version)/build"

  echo "Installing build files..."
  install -Dt "$builddir" -m644 .config Makefile Module.symvers System.map \
    localversion.* version vmlinux tools/bpf/bpftool/vmlinux.h
  install -Dt "$builddir/kernel" -m644 kernel/Makefile
  install -Dt "$builddir/arch/x86" -m644 arch/x86/Makefile
  cp -t "$builddir" -a scripts
  ln -srt "$builddir" "$builddir/scripts/gdb/vmlinux-gdb.py"

  # required when STACK_VALIDATION is enabled
  install -Dt "$builddir/tools/objtool" tools/objtool/objtool

  # required when DEBUG_INFO_BTF_MODULES is enabled
  install -Dt "$builddir/tools/bpf/resolve_btfids" tools/bpf/resolve_btfids/resolve_btfids

  echo "Installing headers..."
  cp -t "$builddir" -a include
  cp -t "$builddir/arch/x86" -a arch/x86/include
  install -Dt "$builddir/arch/x86/kernel" -m644 arch/x86/kernel/asm-offsets.s

  install -Dt "$builddir/drivers/md" -m644 drivers/md/*.h
  install -Dt "$builddir/net/mac80211" -m644 net/mac80211/*.h

  # https://bugs.archlinux.org/task/13146
  install -Dt "$builddir/drivers/media/i2c" -m644 drivers/media/i2c/msp3400-driver.h

  # https://bugs.archlinux.org/task/20402
  install -Dt "$builddir/drivers/media/usb/dvb-usb" -m644 drivers/media/usb/dvb-usb/*.h
  install -Dt "$builddir/drivers/media/dvb-frontends" -m644 drivers/media/dvb-frontends/*.h
  install -Dt "$builddir/drivers/media/tuners" -m644 drivers/media/tuners/*.h

  # https://bugs.archlinux.org/task/71392
  install -Dt "$builddir/drivers/iio/common/hid-sensors" -m644 drivers/iio/common/hid-sensors/*.h

  echo "Installing KConfig files..."
  find . -name 'Kconfig*' -exec install -Dm644 {} "$builddir/{}" \;

  echo "Removing unneeded architectures..."
  local arch
  for arch in "$builddir"/arch/*/; do
    [[ $arch = */x86/ ]] && continue
    echo "Removing $(basename "$arch")"
    rm -r "$arch"
  done

  echo "Removing documentation..."
  rm -r "$builddir/Documentation"

  echo "Removing broken symlinks..."
  find -L "$builddir" -type l -printf 'Removing %P\n' -delete

  echo "Removing loose objects..."
  find "$builddir" -type f -name '*.o' -printf 'Removing %P\n' -delete

  echo "Stripping build tools..."
  local file
  while read -rd '' file; do
    case "$(file -Sib "$file")" in
      application/x-sharedlib\;*)      # Libraries (.so)
        strip -v $STRIP_SHARED "$file" ;;
      application/x-archive\;*)        # Libraries (.a)
        strip -v $STRIP_STATIC "$file" ;;
      application/x-executable\;*)     # Binaries
        strip -v $STRIP_BINARIES "$file" ;;
      application/x-pie-executable\;*) # Relocatable binaries
        strip -v $STRIP_SHARED "$file" ;;
    esac
  done < <(find "$builddir" -type f -perm -u+x ! -name vmlinux -print0)

  echo "Stripping vmlinux..."
  strip -v $STRIP_STATIC "$builddir/vmlinux"

  echo "Adding symlink..."
  mkdir -p "$pkgdir/usr/src"
  ln -sr "$builddir" "$pkgdir/usr/src/$pkgbase"
}

pkgname=(
  "$pkgbase"
  "$pkgbase-headers"
)
for _p in "${pkgname[@]}"; do
  eval "package_$_p() {
    $(declare -f "_package${_p#$pkgbase}")
    _package${_p#$pkgbase}
  }"
done

# vim:set ts=8 sts=2 sw=2 et:
