# Contributor: Nicky726 (nicky726 <at> gmail <dot> com)
pkgname=e17-icons
pkgver=20130331
pkgrel=1
pkgdesc="Animated icons for E17 from exchange.enlightenment.org"
arch=('any')
url="http://exchange.enlightenment.org/themeGroup/show/5064"
license=('Unknown')
depends=('enlightenment17')
makedepends=('wget')
source=()
md5sums=()

# Base URL for the icons.
_iconsbase="http://exchange.enlightenment.org/theme/get"

# Array of "id:name" values,
# where id is the theme id at http://exchange.enlightenment.org/.
# Use '_' instead of ' ' in names;
# they will be replaced when printed to stdout.

_icons=(
2024:Xchat2
1754:Xchat
1764:Thunar
1784:Terminal_Tango
1794:Terminal_Gant
1774:Terminal
1934:Opera
1944:Notes
1954:Listen
2034:Iceweasel
1964:Icedove_Simple
2044:Icedove
1974:Globe
1984:Gimp
1994:Firefox_Plain
2004:Firefox
2054:Elpanel
2014:Burner
2064:Audio_Player
2264:PTTerminal
2274:Metronome
2254:Red_USB
2483:PTTCalendar
2619:FirefoxTT
2625:MPlayer
)


package() {
  cd "${srcdir}"

  for _icon in ${_icons[@]}
  do

    # Separate name and icon id.
    _name=${_icon#*:} # Remove icon "id:"
    _name=${_icon//_/ } # Replace '_' by ' '
    _id=${_icon%%:*} # Remove icon ":name"

    echo
    echo
    echo "----------------------------------------------------------------"
    echo "*** Downloading icon '${_name}'..."
    echo

    # Upstream sends themes under the numerical code, missuse -O to workaround
    wget -O "${_icon#*:}.edj" -c "${_iconsbase}/${_id}" ||
    echo 2>&1 "### Error downloading icon '${_name}'."

  done

  # Prepare package directory structure
  install -m755 -d "${pkgdir}/usr/share/enlightenment/data/icons"

  # Install the edjs
  install -m644 *.edj "${pkgdir}/usr/share/enlightenment/data/icons"
}
