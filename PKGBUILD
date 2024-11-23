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
pkgver=6.12.1
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
        #https://www.kernel.org/pub/linux/kernel/v6.x/patch-${pkgver}.xz
        config
        # Upstream Patches
        # ARCH Patches
        0101-ZEN_Add_sysctl_and_CONFIG_to_disallow_unprivileged_CLONE_NEWUSER.patch
        0102-drivers-firmware-skip-simpledrm-if-nvidia-drm.modese.patch
        0103_default_to_max_ASLR_bits.patch
        # Realtek patch
        0999-patch_realtek.patch
        # ROG ALLY Patches (wip/ally-6.12)
        0001-Input-xpad-add-support-for-ASUS-ROG-RAIKIRI-PRO.patch
        0002-platform-x86-asus-wmi-don-t-fail-if-platform_profile.patch
        0003-acpi-x86-s2idle-add-support-for-screen-off-and-scree.patch
        0004-drm-Notify-the-suspend-core-when-displays-are-change.patch
        0005-acpi-x86-s2idle-Move-screen-off-on-code-into-dedicat.patch
        0006-platform-x86-asus-wmi-Refactor-Ally-suspend-resume.patch
        0007-mt7921e_Perform_FLR_to_recovery_the_device.patch
        0007-platform-x86-asus-wmi-export-symbols-used-for-read-w.patch
        0008-hid-asus-Add-MODULE_IMPORT_NS-ASUS_WMI.patch
        0009-platform-x86-asus-armoury-move-existing-tunings-to-a.patch
        0010-platform-x86-asus-armoury-add-panel_hd_mode-attribut.patch
        0011-platform-x86-asus-armoury-add-the-ppt_-and-nv_-tunin.patch
        0012-platform-x86-asus-armoury-add-dgpu-tgp-control.patch
        0013-platform-x86-asus-armoury-add-apu-mem-control-suppor.patch
        0014-platform-x86-asus-armoury-add-core-count-control.patch
        0015-platform-x86-asus-wmi-deprecate-bios-features.patch
        0016-ALSA-hda-realtek-fixup-ASUS-GA605W.patch
        0017-hid-asus-ally-Add-joystick-LED-ring-support.patch
        0018-hid-asus-ally-initial-Ally-X-gamepad.patch
        0019-hid-asus-ally-initial-gamepad-configuration.patch
        0020-hid-asus-ally-add-button-remap-attributes.patch
        0021-hid-asus-ally-add-gamepad-mode-selection.patch
        0022-hid-asus-ally-Turbo-settings-for-buttons.patch
        0023-hid-asus-ally-add-vibration-intensity-settings.patch
        0024-hid-asus-ally-add-JS-deadzones.patch
        0025-hid-asus-ally-add-trigger-deadzones.patch
        0026-hid-asus-ally-add-anti-deadzones.patch
        0027-hid-asus-ally-add-JS-response-curves.patch
        0028-hid-asus-ally-add-calibrations-wip.patch
        0029-debug-by-default.patch
        0030-hda-tas2781-add-speaker-id-check-for-ASUS-projects.patch::https://lore.kernel.org/lkml/20241116075006.11994-1-baojun.xu@ti.com/raw
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
            '050da549692f5ec1404edf067550f4296521810858479c794ff177a706c159ab'
            '888a89ec67433ddfd71ba187a7356ca60270dbe51d6df7211e3930f13121ba8c'
            '934bc233684c45860251bb75433d671b23fa784c891ab3a1ef10d5bc761156b6'
            '6400a06e6eb3a24b650bc3b1bba9626622f132697987f718e7ed6a5b8c0317bc'
            'b88d42565ce771cb6c8f98b7c05aada6b8024578a1985e5772dc5a2d07facee0'
            '9732e024f477dcd918d9ffda33dc4ba04bf6b7b9efa54d899a790423ffa45066'
            '20286f5b8b68e88f0ec78b2d946f1dd80aa180719fb2bcc6548cc0637450f1e3'
            '66b291495f91770d411b66cd64a471fd8fa43d72933309dcee61d888b0d06be6'
            'db2df7d923f5eecf52d4520222cda9613593566cbb6b65d509b02329fc37aa9f'
            '9e74bed6ec75185b044296b62d443843dae5d817a55a7aee2cb2eb8a9908d2ca'
            'd16e5a1e2addc7a3950b0737788939e21f0ae25d8cbf17be5176194a7f97428f'
            'd673d034fbcd80426fd8d9c6af56537c5fe5b55fe49d74e313474d7fc285ecc1'
            'a4b0cfa112115fe7d48f5891c97a500619def58173ee93e8b8e959d4696d8141'
            '43a6476c994de7090a280f264119402a84dbf475508750a8c5beddd3014d7fa1'
            'b548b95b2b3cf36d2281070b3ea22033fbb96eb31c3bba5f17517f39fa16ffec'
            '40ed24aea624146cbcfc5cfd5d79008b72b38fc506c66383836e2d3bf2313c11'
            '6342f0bd434143ec7aa1dd3c710549ff86bbce5013bc8086cdc63edbd57d7bd8'
            '21d36caa24427307901b903c184378ec7a63ebd5e59618fdd149481687a0634e'
            '00b6681af8edaefaef2077f41a1e0fcb96577789b031e477edd5bb199feb7e44'
            '9fb2b28fd17381fc3029b5f99a3e9ff753cf5490e7dce7e0cb0e241e2c6b2028'
            '5afe9edbfed23e2e9b535d05bdfb02bb137bc1e5d727e5a7d6bb342dfbc1778e'
            '3f0e5d8ba9c8aef53987ec2f3aa00499cb29ea5a3d079fea5ee6d96e36df5b0d'
            '5f4dabed31825b4aebe32a5c5be64b6422035f252e8192755c900ccca4e87915'
            '20259c7a24d99dfe0d31f7dee3a3490660c6c5c5e0785c03b1feec96376b9dfd'
            '1ce01fafcf1a229b31f90b39d027d82019cb98cc3dbac6994fa9c2ca958c47a8'
            'd5c85e7c5b6616d0e19ce5b1b4b9932587f086a834c85cd98ee48208f5056114'
            'f2d23e35d6f00582513132b7457893304876f1b2ff13a3e6b8108d905f5978a3'
            'b54e57ffa0a7be056facef4d456a51b2423445ea80bede2eb11aa81f7bcc9117'
            '4e5e3cb197abd5db0f04319e6874effa88a6d0c96a3a57c88c8f6f7e076acaaf'
            '844a7909e44701bfe0ab7cf7a7d692f64d482efcb1a71397e2ce46e72a49c0f8'
            'faa97b095381e8ea555d33e6f57ec3113a31909792df7d8a9074c224070be362'
            '3ffabba0f5d1d7bc6b7e5158c990eb28360a6ba86bbe9d551fdb98692bb86f9f'
            '8b22af5ac8eff69aaf374403e6aa515e52ca449191c8bfd75da98a4bed200ffb'
            '904b87f704dcb1db1ecc1fc692947c937500d51e8a92c5c57a9578fec10c116f'
            '32a79a85597516e58f76c0ebdfc78d89df359aebf274eb70a31f280c510710de'
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
