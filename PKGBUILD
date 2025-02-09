# Maintainer: Bernhard Landauer <bernhard@manjaro.org>
# Maintainer: Philip Müller <philm[at]manjaro[dot]org>
# Archlinux maintainers:
# Tobias Powalowski <tpowa@archlinux.org>
# Thomas Baechler <thomas@archlinux.org>

_basekernel=6.12
_basever=${_basekernel//.}
_kernelname=-MANJARO
_commit=
_rc=
pkgbase=linux${_basever}
pkgver=6.12.13
pkgrel=2
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
source=("https://www.kernel.org/pub/linux/kernel/v6.x/linux-${_basekernel}.tar.xz"
        #https://github.com/torvalds/linux/archive/refs/tags/v${_basekernel}.tar.gz
        #https://github.com/torvalds/linux/archive/refs/tags/v${_basekernel}-${_rc}.tar.gz
        #https://github.com/torvalds/linux/archive/${_commit}.tar.gz
        https://www.kernel.org/pub/linux/kernel/v6.x/patch-${pkgver}.xz
        config
        # ARCH Patches
        0101-ZEN_Add_sysctl_and_CONFIG_to_disallow_unprivileged_CLONE_NEWUSER.patch
        0102-drivers-firmware-skip-simpledrm-if-nvidia-drm.modese.patch
        0103_default_to_max_ASLR_bits.patch
        # Realtek patch
        0999-patch_realtek.patch
        # ROG ALLY Patches (wip/ally-6.12)
        0001-Tmp-add-GA605W-H7606W-to-AMD-PMF-quirks.patch
        0002-hid-asus-Disable-OOBE-mode-on-the-ProArt-P16.patch
        0003-platform-x86-asus-wmi-Remove-all-ROG-Ally-CSEE-hacks.patch
        0004-platform-x86-asus-wmi-export-symbols-used-for-read-w.patch
        0005-hid-asus-check-ROG-Ally-MCU-version-and-warn.patch
        0006-asus-wmi-disable-mcu_powersave-if-MCU-version-too-lo.patch
        0007-hid-asus-ally-Add-joystick-LED-ring-support.patch
        0008-hid-asus-ally-initial-Ally-X-gamepad.patch
        0009-hid-asus-ally-initial-gamepad-configuration.patch
        0010-hid-asus-ally-add-button-remap-attributes.patch
        0011-hid-asus-ally-add-gamepad-mode-selection.patch
        0012-hid-asus-ally-Turbo-settings-for-buttons.patch
        0013-hid-asus-ally-add-vibration-intensity-settings.patch
        0014-hid-asus-ally-add-JS-deadzones.patch
        0015-hid-asus-ally-add-trigger-deadzones.patch
        0016-hid-asus-ally-add-anti-deadzones.patch
        0017-hid-asus-ally-add-JS-response-curves.patch
        0018-hid-asus-ally-add-calibrations-wip.patch
        0019-debug-by-default.patch
        0020-platform-x86-asus-armoury-move-existing-tunings-to-a.patch
        0021-platform-x86-asus-armoury-add-panel_hd_mode-attribut.patch
        0022-platform-x86-asus-armoury-add-apu-mem-control-suppor.patch
        0023-platform-x86-asus-armoury-add-core-count-control.patch
        0024-platform-x86-asus-wmi-deprecate-bios-features.patch
        0025-drm-amd-display-Avoid-divide-by-zero-by-initializing.patch
        0026-platform-x86-asus-armoury-add-the-ppt_-and-nv_-tunin.patch
        0027-backport-asus-armoury-fix-fw_attributes_class-after-.patch
        0028-backport-asus-wmi-fix-symbol-ASUS_WMI-after-cherry-p.patch
        0029-hda-tas2781-add-speaker-id-check-for-ASUS-projects.patch::https://lore.kernel.org/lkml/20241123073718.475-1-baojun.xu@ti.com/raw
        # OrangePi Neo patches
        0001-iio_imu_Add_driver_for_Bosch_BMI260_IMU.patch
        # Zotac Zone patches
        636de3f2be1d171b50c47b9f038b7a5b19d8667d.patch
        aa776ec5fb0ff9f94cb546773e76a248e05084b5.patch
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

sha256sums=('b1a2562be56e42afb3f8489d4c2a7ac472ac23098f1ef1c1e40da601f54625eb'
            'c2e499626215976b6548e48a633c2d28469751e0dd2109e4c1ae6d6055406fc6'
            'e243707747eb111e1579ffc7ae6c1587e4d906303e7d5d38d8c2b1446b99d9bd'
            '888a89ec67433ddfd71ba187a7356ca60270dbe51d6df7211e3930f13121ba8c'
            '934bc233684c45860251bb75433d671b23fa784c891ab3a1ef10d5bc761156b6'
            '6400a06e6eb3a24b650bc3b1bba9626622f132697987f718e7ed6a5b8c0317bc'
            'b88d42565ce771cb6c8f98b7c05aada6b8024578a1985e5772dc5a2d07facee0'
            '5f3d14412b9ea348ad6be2354f1022badc9febe06191e85a228a0c40a84e8f1d'
            '5b50462a0d3a62c52793a54fea736471e71a5de84ec3a37de616acfecf261c26'
            'f4dc0ae6cd9fdefe1607a0017c560308177ef2f3e5f178c99aaa12092f4c6566'
            'cd6d7a2cfffd28fb92bdda134e9f03f3764bb805fe7949e37c16fca64031e163'
            '999c24f868fcde762ec8b03fef3ea03d8fac5a58a16f5aa02fdcbccf18507168'
            'a13bb79244a91b4261cee7d45d85e7729f6098699223072f03b7dc36b69acf3d'
            '314507f5bd9efcca79b72cfdcbda62fedcd851d9161e99d1bfee4875a0a58d8b'
            '8215c128f5c1a6c17383f647f79db9dc38c9efeea7032c73e8906f1f941c79cb'
            'a89467290a127d416e6aea2d298576f72a5d50896485a413f046072a6ec62002'
            '523daeefdbe2b368032f3943e23ff1a7a52da3f8cfb43b33f181023a56162ac4'
            'b2d1c0068fe1b069f77e8126c7f6d7f14203f9d97779db61e744900bf06eb363'
            '14044c8a525e59628a42870d181f0feaf1fe2b1331ffe4b9f145368b978a2c70'
            'a96f8ebdee9b8ce5676ae27cdc4b4b45cd75f5febc00933f07fb8745b637573b'
            '7bf2336381d7cdd4e3c44bf98650351da2628aeb909c57645bba30961b0a6328'
            '227528033418f94852bf5bd5387ce072d383056b333a76dc8534f496c751ba1e'
            '366c02ab50464e30b8d2c0226f6c564e7bf972b97006a37c31df3428279774cb'
            '88763f2db4de0e30d0ad5bc8e78ba987e98c662928cb68ddb3f2d202bd0e8665'
            '2f52da9e96926be1395ddfba0fd902f5eb173626960a9ceee2c70c67572494df'
            '560ef6b4ac29cb1f743b5666119a179e6187fe160765f8a519c45701eda6dd9e'
            '88682388ebf70ed3bd778314ea9b7606d2275774a7188946759c3b53b41a96ac'
            'c4d444a07e21ff4e8222041e1d54118374b941ebf17eb539f6538187660dee75'
            '9c8412256aa4a2763e5b6a642a29926b2488441a204932f5f62cf4c4f43d570b'
            '80f3d84c0c74449b31a15f33b4e3808d95417bb19bebd5e621ce6df878cac784'
            'd91ff7d013ffe576711e478d1212894c91ebeee88921ea102adc7d077e601b0c'
            '5633134cff2f296a1de8656cc80a2dfc0ebd6532903ea4a7b71f8452b5684f3a'
            'b2e5cdce56aaf1ad7013968189823a1a5663ba50f81e0098ca53cfd7bd6c6332'
            'eda26710ffe67fc824e0306c54e0d3db1273c8aca2e5e8754f9048fe91850a2d'
            'b63db26a99071332169209dcc769df0909e311e0f319d456d4f5892bc54998f3'
            '353af1b0411c4400277cf49270d1183e1678d46e5a77ea043be948fa1cbb9db2'
            'e58b6631da6dcc302984c30882276026a449228833cfb01d157a85ff1064080e'
            '5dabdb1d45f1edd9bfaeebbc4a8767812fae5b4de9866cedecab7bfcf982b8ee'
            '4a9d290f020ff88617ecb7c2aa38ecee796dc800b677dd2fa9c8f64797a33aa0'
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
  provides=("linux-headers=$pkgver")

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
