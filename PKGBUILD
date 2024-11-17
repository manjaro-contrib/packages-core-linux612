# Maintainer: Bernhard Landauer <bernhard@manjaro.org>
# Maintainer: Philip Müller <philm[at]manjaro[dot]org>
# Archlinux maintainers:
# Tobias Powalowski <tpowa@archlinux.org>
# Thomas Baechler <thomas@archlinux.org>

_basekernel=6.12
_basever=${_basekernel//.}
_kernelname=-MANJARO
_commit=4a5df37964673effcd9f84041f7423206a5ae5f2
_rc=rc7
pkgbase=linux${_basever}
pkgver=6.12.0rc7
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
        # ROG ALLY Patches (work-branch)
        #0001-Fix-ROG-ALLY-X-audio.patch
        #0002-platform-x86-asus-wmi-add-support-for-vivobook-fan-p.patch
        #0003-hid-asus-use-hid-for-brightness-control-on-keyboard.patch
        0004-Input-xpad-add-support-for-ASUS-ROG-RAIKIRI-PRO.patch
        #0005-platform-x86-asus-wmi-add-debug-print-in-more-key-pl.patch
        #0006-platform-x86-asus-wmi-don-t-fail-if-platform_profile.patch
        0007-acpi-x86-s2idle-add-support-for-screen-off-and-scree.patch
        0008-drm-Notify-the-suspend-core-when-displays-are-change.patch
        0009-acpi-x86-s2idle-Move-screen-off-on-code-into-dedicat.patch
        0010-platform-x86-asus-wmi-Refactor-Ally-suspend-resume.patch
        0011-platform-x86-asus-wmi-export-symbols-used-for-read-w.patch
        0012-hid-asus-Add-MODULE_IMPORT_NS-ASUS_WMI.patch
        0013-platform-x86-asus-armoury-move-existing-tunings-to-a.patch
        0014-platform-x86-asus-armoury-add-panel_hd_mode-attribut.patch
        0015-platform-x86-asus-armoury-add-the-ppt_-and-nv_-tunin.patch
        0016-platform-x86-asus-armoury-add-dgpu-tgp-control.patch
        0017-platform-x86-asus-armoury-add-apu-mem-control-suppor.patch
        0018-platform-x86-asus-armoury-add-core-count-control.patch
        0019-platform-x86-asus-wmi-deprecate-bios-features.patch
        #0020-ACPI-PM-Quirk-ASUS-ROG-M16-to-default-to-S3-sleep.patch
        #0021-ACPI-CPPC-Add-support-for-setting-EPP-register-in-FF.patch
        #0022-Bluetooth-btusb-Add-2-USB-HW-IDs-for-MT7925-0xe118-e.patch
        #0023-ALSA-hda-realtek-fixup-ASUS-GA605W.patch
        0024-hid-asus-ally-Add-joystick-LED-ring-support.patch
        0025-hid-asus-ally-initial-Ally-X-gamepad.patch
        0026-hid-asus-ally-initial-gamepad-configuration.patch
        0027-hid-asus-ally-add-button-remap-attributes.patch
        0028-hid-asus-ally-Turbo-settings-for-buttons.patch
        0029-hid-asus-ally-add-gamepad-modes-and-defaults.patch
        0030-hid-asus-ally-add-vibration-intensity-settings.patch
        0031-hid-asus-ally-add-JS-deadzones.patch
        0032-hid-asus-ally-add-trigger-deadzones.patch
        0033-hid-asus-ally-add-anti-deadzones.patch
        0034-hid-asus-ally-add-JS-response-curves.patch
        0035-hid-asus-ally-add-calibrations-wip.patch
        0036-hda-tas2781-add-speaker-id-check-for-ASUS-projects.patch::https://lore.kernel.org/lkml/20241116075006.11994-1-baojun.xu@ti.com/raw
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

sha256sums=('cc0d7c53e1aec1790ccc717ce173edfa6d6b82feaa883ca746336ad729c465a6'
            '9e497349762ccdf9037575a07142bc082d356c0594466f1f601e389159cfc71f'
            '888a89ec67433ddfd71ba187a7356ca60270dbe51d6df7211e3930f13121ba8c'
            '934bc233684c45860251bb75433d671b23fa784c891ab3a1ef10d5bc761156b6'
            '6400a06e6eb3a24b650bc3b1bba9626622f132697987f718e7ed6a5b8c0317bc'
            'b88d42565ce771cb6c8f98b7c05aada6b8024578a1985e5772dc5a2d07facee0'
            'e06d2440897987d9bdce107dd1bed97df07e82591da2600e1771f383dea5faed'
            'c0f23800fa79d8c268c54a10503d43482012c159376980b8ffcab85e50d36aaa'
            '27fa260443d439e4b346ede3018ce57a6f09548b807a95ebb38fa1d446ac0601'
            '2c644704fcf8dddef5df7368699d70a95af7567764b36997c1b4271d1d018130'
            'd04b4c925a83d5ce760bd4cb738fed306406c9cbca37fa173aaa3f136d3fb68d'
            '3b6e6094cc81131c57e60bc2d6f2852954cb68dbcd3c5e1304686f56c3cae96a'
            '576e6e9ab5bf486db39ad37a9b326de76a0a611149dfcde2fb3c1fccde5475fe'
            '6e41489b469fafa717970318abe5cc5f6c0c781f33a4180dc8af9159c6eb819d'
            'c222e0c245f3bc0592e8de40a1cb84c26f2d94b8fa583428455b4c69f65542d9'
            '2bc9b47a75073a6eb9128c794c4f2ea02a2fe88067993991d1c0802ce0611e4b'
            'b31e3e48e37693f5d9a18643a8a14806cbd3d9d15d595cd822aea25d4f57a2e6'
            '6a583d8720a36ae61a6912b580ea06e1854d75a1d3633801413feb93e7dad039'
            'bfd7af0e37faca28ecbefbd4240a6fc821da8b029e3f2eb594b31283bc54b3e9'
            '8ee2332f0753ff9b575c5f055d166673c2536838ea86aa2962e274d3d94b309a'
            'c7f4babcc81a98cc90d132667a64f46b59ab51954eb19de2e5694a3510f50244'
            'b89a90e0c536b9fe6425ebc712275c88118674dfb0d18b2f7f497cecb0d86b7d'
            '9e7cc9855aa75c59e554d4534476f6038e43c06bf31925e84c15d3a768e9d0aa'
            '12c84b7bed1661ed1fcb637ba65878e32ae63962145cdb2000b2357cd82f87dc'
            'b00c956069b5d1b901d74e62cf52e4b8944b72bc5a0da8b7631bd03c9af6ad45'
            'cca275f5fd132ebce8eaf750461e501543f4495b9930733874dfb99c3a5feaec'
            'f544f5583a36fbae9b1f1c899b0e526a9613edd1b444eb8ff110b48d95e5dece'
            '2fdda123372e610011ff7453c5d59f5083c50048127be26a89f73515d4f69d32'
            'bca273a6ce4bba9db1fad5f71f95bd48a37aa345c433203db37f4372c0ea134c'
            '6bd3eeea07f47fd2e1810426750a13426cb20ea5a505c595d41bb428ad2e3437'
            '489ec97424261e2e4f4307e25ed9c501d88e3c3a4c23e3928cc0150acff3d520'
            '38168d0ce594da13917cc86590bd92848a96c7e6dfb1170e06d0d53a84a04dea'
            'ec271de821e530fc673faba3468858bd49956ba3a3ec596b74cfb4584cf5c6d5'
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
