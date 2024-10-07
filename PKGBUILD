# Maintainer: Bernhard Landauer <bernhard@manjaro.org>
# Maintainer: Philip Müller <philm[at]manjaro[dot]org>
# Archlinux maintainers:
# Tobias Powalowski <tpowa@archlinux.org>
# Thomas Baechler <thomas@archlinux.org>

_basekernel=6.12
_basever=${_basekernel//.}
_kernelname=-MANJARO
_commit=
_rc=rc2
pkgbase=linux${_basever}
pkgname=("$pkgbase" "$pkgbase-headers")
pkgver=6.12.0rc2
pkgrel=1
arch=('x86_64')
url="https://www.kernel.org/"
license=('GPL2')
makedepends=(bc docbook-xsl libelf pahole python-sphinx git inetutils kmod xmlto cpio perl tar xz rust rust-bindgen rust-src)
options=('!strip')
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
        0024-Initial-gamepad-key-mapping-pre-refactor.patch
        0025-First-pass-refactor.patch
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

sha256sums=('36efbb865ead39771f63ecad7a26adf3dc7de93e27932e59dda81a0bda556b91'
            '45754752e7bfd0ad3b230a88df04dea58afb1c700d9d3933849d893e65fb3101'
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
            '299715687865262c27208360fe7fb99e41c42f02e212ecd2518dd669d7227b77'
            'dc0c20aeae0f7f2f55cd197a60dcd5d1f3ad552cf56438423a0903ec3a18b6b7'
            '947b275256b64eab81f9d58c33ff0a955b45dc0fbd79d7bca0ea28b5b70ee0aa'
            '3c9ad2bbcc3d63e4eb4e0061648bab10cf9b2fcc82f122949700aa24fb44f996'
            '9495d00b330c7e1fb320a13c438dc032c7140e6c1408181b3bc858d71f47a7c7'
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
