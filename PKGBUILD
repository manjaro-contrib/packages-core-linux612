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
pkgver=6.12.90
pkgrel=1
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
        # Upstream Patches
        # https://lore.kernel.org/linux-bluetooth/01ffb0cc-dcf6-4e60-adf3-fbb96e0666d0@leemhuis.info/
        0001-Bluetooth-btmtk-accept-too-short-WMT-FUNC_CTRL-events.patch
        # ARCH Patches
        0101-ZEN_Add_sysctl_and_CONFIG_to_disallow_unprivileged_CLONE_NEWUSER.patch
        0102-drivers-firmware-skip-simpledrm-if-nvidia-drm.modese.patch
        # Realtek patch
        0999-patch_realtek.patch
        # ROG ALLY Patches (wip/ally-6.12)
        0001-drm-amd-display-Avoid-divide-by-zero-by-initializing.patch
        0002-Tmp-add-GA605W-H7606W-to-AMD-PMF-quirks.patch
        revert-upstream-hid-asus-check-ROG-Ally-MCU-version-and-warn.patch
        0004-hid-asus-check-ROG-Ally-MCU-version-and-warn.patch
        0005-platform-x86-asus-wmi-Refactor-Ally-suspend-resume.patch
        0006-hid-asus-set-mcu-hack-to-off-if-required-MCU-version.patch
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
        0018-hid-asus-ally-mcu_version-attribute.patch
        0019-hid-asus-ally-add-calibrations-wip.patch
        0020-hid-asus-ally-set-default-backface-btns-to-F14-15.patch
        0021-debug-by-default.patch
        0022-platform-x86-asus-wmi-export-symbols-used-for-read-w.patch
        0023-platform-x86-asus-armoury-move-existing-tunings-to-a.patch
        0024-platform-x86-asus-armoury-add-panel_hd_mode-attribut.patch
        0025-platform-x86-asus-armoury-add-apu-mem-control-suppor.patch
        0026-platform-x86-asus-armoury-add-core-count-control.patch
        0027-platform-x86-asus-wmi-deprecate-bios-features.patch
        0028-platform-x86-asus-armoury-add-the-ppt_-and-nv_-tunin.patch
        0029-backport-asus-armoury-fix-fw_attributes_class-after-.patch
        0030-backport-asus-wmi-fix-symbol-ASUS_WMI-after-cherry-p.patch
        0031-hda-tas2781-add-speaker-id-check-for-ASUS-projects.patch::https://lore.kernel.org/lkml/20241123073718.475-1-baojun.xu@ti.com/raw
        # OrangePi Neo patches
        0001-iio_imu_Add_driver_for_Bosch_BMI260_IMU.patch
)

if [[ ! -z "$_commit" ]]; then
  _srcdir="linux-${_commit}"
elif [[ ! -z "$_rc" ]]; then
  _srcdir="linux-${_basekernel}-${_rc}"
else
  _srcdir="linux-${_basekernel}"
fi

sha256sums=('b1a2562be56e42afb3f8489d4c2a7ac472ac23098f1ef1c1e40da601f54625eb'
            '0da1c69fcab6e169873c54cda24b67c78d4760ee8b0f07679e4e785c5eae325f'
            'e89b62a38fa1d758771c855767ba074738a7e5e333481992b64dec80bfe0658c'
            '9f4a608ea5ff6f119f1448ddac1917e11b6eb3d696d18f2b5e934a1c8e3f3d65'
            '888a89ec67433ddfd71ba187a7356ca60270dbe51d6df7211e3930f13121ba8c'
            '934bc233684c45860251bb75433d671b23fa784c891ab3a1ef10d5bc761156b6'
            'b88d42565ce771cb6c8f98b7c05aada6b8024578a1985e5772dc5a2d07facee0'
            'c5288dd3057ced81018db254c94fd7ee8dfc5d4687064b5ae234d56f04ad1069'
            'a4ec35907f4d532b45599821a74e7703e21a4df1677a3c057c433d13b31816a4'
            '8a4765598fd6090a5cbfddb40470362d99968463a47e605f9ee4e45be06d25c0'
            'a1c2e372d771b1bd42cb5f1e51718ea2c8af4fa911f4fd640d8d10cbf1e59cb0'
            '76eb9ac8f1a9928fa1f2222171633801898a5f89a139241443ec3c7df46b8531'
            '7893450bfae2bba7a1d20d29ad1791cadde32197297acb84bbbed1d952d24052'
            '5a5a0f80e76b693f0e06d1644bb81b0f3720fca7e14435fc06ecfaa187380602'
            '3fac0fb57c769bfef57d71d78d1b5f681947c2146ef30d7a9afdc87805eda058'
            '20e07201d951773ff60b9b4f201bf21386ea3102a80e4a158bbaeb7bc1ae1b45'
            '5b515dc4e43f5e3638a9f09318361c2f26964612df511d54a41149147926c40d'
            'b7118bb15b6c8f591d726dab469a2b7e48693d61c534e950eeb8dd5e4f45900f'
            'da11bacca3788f18f1267eef5453018f8c3b358c9e5b43e6242b5529e09237fc'
            'b3a36f8e02c78c953b738c4d2ecb59c8a84dfce5a354ee8f1d8d30c07e3e904d'
            'a706c396738153983140dae0d7322170920557dcb7852cbbb6392f8dfe4d72b9'
            '77413e58e83c14d01035d14aa4483df5da7ab3c8051eb8dda8df1ee9f1e18192'
            'a9c52bd8c76dbb4d65591534e34666bf95db698ad614672d3981c3667fdea8f9'
            'd7f139f1957b83f9954cb9f5a801f07ab0db3cb9f6a20206e1b7c988e1d3339b'
            '9e818853ede7775c809cff9de640b722d915f628817e6c9538fa5e6c8a4ea016'
            '9924ceda71fc126118d51cd8e23b46cc7e374b99bf08ffa035a46f878b3b5ac3'
            '99b1c4b1eac5d7cf6dd4fcc27488a14a7b4e79891f3285002dd3eb02d64f493b'
            '8aef981bda2f6406b48f428a2ad105d69d3c7114fe727f7f1ab81a44b8a1f9fc'
            'fef19b5e6adeac38e1a09c9323420da1a134cb4bb10c38610f0779c3cd4bef20'
            'bd81d17e0762553fbfeb27d8ef98f34e6897d26fc113940d0002fda481fb5de0'
            'e63ed6514de8d83fd16bafe9f7037aed8da25c8763b5153083290870410dd7c5'
            '6ecd696e2ea3ef53789e24370c2b155bc51a9c17854a7c273cec5c1cc4b3bc51'
            '78954076a9e6ce21be2bcb0dea717a9b2992c4cf55a4c95922000358be3ec5c9'
            '7ac1742354ca76bf89a2ef2b61136fb41c72ed4303047843d60b66d4d7383822'
            '26ab54dcfd68069008b5b19983f20ba954a5e311e6420f2783dec5a912493996'
            '9baa3f0cad34916f0599efeaa67170ee470f0ca1453666aa2e37bc62a843f277'
            '69be0b12d0df47866b65d969f1354acda58fb09d576763431ec3b1bc120c7cf1'
            '353af1b0411c4400277cf49270d1183e1678d46e5a77ea043be948fa1cbb9db2'
            'e58b6631da6dcc302984c30882276026a449228833cfb01d157a85ff1064080e')

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
    'coreutils'
    'initramfs'
    'kmod'
  )
  optdepends=(
    'linux-firmware: firmware images needed for some devices'
    'scx-scheds: to use sched-ext schedulers'
    'wireless-regdb: to set the correct wireless channels of your country'
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
