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
pkgver=6.12.5
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
        # https://gitlab.freedesktop.org/drm/amd/-/issues/3831
        0001-amdgpu-uvd-get-ring-reference-from-rq-scheduler.patch::https://github.com/torvalds/linux/commit/47f402a3e08113e0f5d8e1e6fcc197667a16022f.patch
        # Realtek patch
        0999-patch_realtek.patch
        # ROG ALLY Patches (wip/ally-6.12)
        0001-Input-xpad-add-support-for-ASUS-ROG-RAIKIRI-PRO.patch
        0002-platform-x86-asus-wmi-don-t-fail-if-platform_profile.patch
        0003-platform-x86-asus-wmi-Refactor-Ally-suspend-resume.patch
        0004-platform-x86-asus-wmi-export-symbols-used-for-read-w.patch
        0005-hid-asus-Add-MODULE_IMPORT_NS-ASUS_WMI.patch
        0006-platform-x86-asus-armoury-move-existing-tunings-to-a.patch
        0007-platform-x86-asus-armoury-add-panel_hd_mode-attribut.patch
        0008-platform-x86-asus-armoury-add-the-ppt_-and-nv_-tunin.patch
        0009-platform-x86-asus-armoury-add-dgpu-tgp-control.patch
        0010-platform-x86-asus-armoury-add-apu-mem-control-suppor.patch
        0011-platform-x86-asus-armoury-add-core-count-control.patch
        0012-platform-x86-asus-wmi-deprecate-bios-features.patch
        0013-ALSA-hda-realtek-fixup-ASUS-GA605W.patch
        0014-hid-asus-ally-Add-joystick-LED-ring-support.patch
        0015-hid-asus-ally-initial-Ally-X-gamepad.patch
        0016-hid-asus-ally-initial-gamepad-configuration.patch
        0017-hid-asus-ally-add-button-remap-attributes.patch
        0018-hid-asus-ally-add-gamepad-mode-selection.patch
        0019-hid-asus-ally-Turbo-settings-for-buttons.patch
        0020-hid-asus-ally-add-vibration-intensity-settings.patch
        0021-hid-asus-ally-add-JS-deadzones.patch
        0022-hid-asus-ally-add-trigger-deadzones.patch
        0023-hid-asus-ally-add-anti-deadzones.patch
        0024-hid-asus-ally-add-JS-response-curves.patch
        0025-hid-asus-ally-add-calibrations-wip.patch
        0026-debug-by-default.patch
        0027-hda-tas2781-add-speaker-id-check-for-ASUS-projects.patch::https://lore.kernel.org/lkml/20241123073718.475-1-baojun.xu@ti.com/raw
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

sha256sums=('b1a2562be56e42afb3f8489d4c2a7ac472ac23098f1ef1c1e40da601f54625eb'
            'ff1db6fd2cf36772bc9136f96062ec6b3fff7d6858a512b6a446731dc242f10d'
            '050da549692f5ec1404edf067550f4296521810858479c794ff177a706c159ab'
            '888a89ec67433ddfd71ba187a7356ca60270dbe51d6df7211e3930f13121ba8c'
            '934bc233684c45860251bb75433d671b23fa784c891ab3a1ef10d5bc761156b6'
            '6400a06e6eb3a24b650bc3b1bba9626622f132697987f718e7ed6a5b8c0317bc'
            '861fe92258827ccd1501dcf969e168408e97cfc64ee16f3abd0ba504ade353b3'
            'b88d42565ce771cb6c8f98b7c05aada6b8024578a1985e5772dc5a2d07facee0'
            'dbe849d61f464b1e6addab0f907a24ebd658251f6177ef21c8e19efbd33dcb59'
            '8561f1318d5b21a396a47c54c0dd03d908518423dd47ab823bb9aa0ff68f4e09'
            '438f26762b03f622794f52a3c3f9d0ab06f950750ead8a740b96dc78f4a817ea'
            'e670b962db827eff431c3ac55fea831d0bc60f3cf94479ca2fc6989c4e4a94ec'
            '368ba0384457f5258ec895b5deb7e2c1efb4954de49e74f2759b0c268623ceaa'
            '452926b2f36397acacf01093aa20aa10aed3bd5e21fce715662387f9079b707a'
            '98cb3dbbbb0ed20d172c1e156c47346eeb8c55109f39aec5071c6fe02bfcbf2e'
            '3daa72402703d8e87f15423090ebb17887374adc5f4d02f8b72ad23dad4ec75a'
            '87e322b16d777309aa8662ccf1fc5e83b827dbeda68ef477c7ae0577bf11257c'
            'b2f8fd486ff94f94ad503d8920a9c4bdd15cd2c7ad17f5ff9fef06d70d59635b'
            '91c9322ee3d41d02d077248ace07841918a1d2454bcb55348afcab69d107619d'
            '371c886fe6228addfbb20ea66ab29b6b24698e8c42e2138dd0534af1821c6e74'
            '942ecde8e199b4dbdb226fb1f6cedbfe3f933afdd86807968efc3db49a80642b'
            'a20765170c1d6d8db250daa68edb34f539619655676115a2e21f0ff0e40a4cf6'
            '6de8cffbe313944ecb2dc9029a8cea80b90d9688cbd6834922bdddfac9efdd64'
            '8f04cf8dba9cebcbb600c46e07f97ec9354fc7d1c262b411a8cd04034e747d2f'
            '7f8b56ec198f0364bd935da4eb1ba4c125ceab2c61983096b959bc39ec2cb21e'
            '204a36a2f204934f644d34df3dd7c711d8179e6a133764bacfd857926755f5f1'
            'f9237f4a87e63c6abeb13a93c883055cfe95b5f7c17190117168d3178836c9ff'
            'ecaaa922e66444722d006351b6f1d8c96976cdb123795b3ae0a1e561317d1e4d'
            '4220fed1e994c811e1f905589c7d041255287d023897df62ae5e04e1f3d46d76'
            '7dbd0e1036df0703b35b99731f673e24e1c6e6d537b3f574e0053feffbf45179'
            'da78fcb7f0592796d6f284c30de316850ee28b1fb40ed15e7fb1303f94732d73'
            'ff81b748591723d307fee8670864d9be22d9bffe4e7edb9f98c1c130668102c4'
            '09283fa299561f7b5f129660bd85f7a98938039ddaec8b178fdb4d640a3deff8'
            'e537ae0480dc3a70f52a0913a21c43c7e7cde6909c472921af07aeabd92339b5'
            '353af1b0411c4400277cf49270d1183e1678d46e5a77ea043be948fa1cbb9db2'
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
