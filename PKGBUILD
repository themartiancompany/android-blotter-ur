# SPDX-License-Identifier: AGPL-3.0

#    -----------------------------------------------------
#    Copyright © 2024, 2025, 2026  Pellegrino Prevete
#
#    All rights reserved
#    -----------------------------------------------------
#
#    This program is free software: you can redistribute
#    it and/or modify it under the terms of the
#    GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of
#    the License, or (at your option) any later version.
#
#    This program is distributed in the hope that it
#    will be useful, but WITHOUT ANY WARRANTY;
#    without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
#    See the GNU Affero General Public License for
#    more details.
#
#    You should have received a copy of the
#    GNU Affero General Public License
#    along with this program.
#    If not, see <https://www.gnu.org/licenses/>.

# Maintainers:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
#   Pellegrino Prevete (dvorak)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
# Contributors:
#   Mark Wagie
#     <mark dot wagie at proton dot me>
#   hexchain
#     <i@hexchain.org>

if [[ ! -v "_docs" ]]; then
  _docs="true"
fi
_py="python"
_proj=hip
_platform=android
_program=blotter
_pkg=${_platform}-${_program}
pkgbase="${_pkg}"
pkgname=(
  "${pkgbase}"
)
if [[ "${_docs}" == "true" ]]; then
  pkgname+=(
    "${_pkg}-docs"
  )
fi
pkgver=0.0.1
_commit="737c0085912f9f7dabf9341d4608e2a77a51a73a"
pkgrel=6
_pkgdesc=(
  "Program which displays text on Android"
  "(a ${_program})."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  'any'
)
_http="https://github.com"
_ns="themartiancompany"
url="${_http}/${_ns}/${_proj}"
license=(
  'Apache-2.0'
)
depends=(
  "termux-shortcuts-utils"
)
makedepends=(
  "make"
)
if [[ "${_docs}" == "true" ]]; then
  makedepends+=(
    "${_py}-docutils"
  )
fi
checkdepends=(
)
provides=(
  "${_program}"
)
_android_blotter_docs_optdepends=(
  "${_pkg}-docs:"
    "Android blotter"
    "documentation"
    "and manuals."
)
_android_blotter_docs_ref_optdepends+=(
 "${_pkg}:"
   "The package this documentation"
   "package pertains to."
)
optdepends=(
  "${_android_blotter_docs_optdepends[*]}"
)
_tag_name="commit"
_tag="${_commit}"
_sum="SKIP"
_sig_sum="SKIP"
_url="${url}"
if [[ "${_tag_name}" == "tag" ]]; then
  _archive_format="tar.gz"
  _url="${_url}/archive/refs/tags/v${_tag}.tar.gz"
elif [[ "${_tag_name}" == "commit" ]]; then
  _archive_format="zip"
  _uri="${_url}/archive/${_commit}.${_archive_format}"
fi
_tarname="${_proj}-${_tag}"
_tarfile="${_tarname}.${_archive_format}"
_src="${_tarfile}::${_uri}"
source=(
  "${_src}"
)
sha256sums=(
  "${_sum}"
)

package_android-blotter() {
  local \
    _make_opts=()
  _make_opts+=(
    PREFIX="/usr"
    DESTDIR="${pkgdir}"
  )
  cd \
    "${_tarname}"
  make \
    "${_make_opts[@]}" \
    install-scripts
  install \
    -Dm644 \
    "COPYING" \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}/"
}

package_android-blotter-docs() {
  local \
    _make_opts=()
  pkgdesc="${pkgdesc} (documentation)"
  depends=()
  optdepends=(
    "${_android_blotter_ref_optdepends[*]}"
  )
  provides=()
  _make_opts+=(
    PREFIX="/usr"
    DESTDIR="${pkgdir}"
  )
  cd \
    "${_tarname}"
  make \
    "${_make_opts[@]}" \
    install-doc \
    install-man
  install \
    -Dm644 \
    "COPYING" \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}/"
}
