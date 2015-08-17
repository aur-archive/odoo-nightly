# Maintainer: Bidossessi Sodonon

pkgname=odoo-nightly
_pkgname=odoo
pkgver=8.0_20150515
pkgrel=1
pkgdesc="Web-based Open Source Business Apps"
url=http://odoo.com/
arch=('any')
license=(GPL3)
provides=("${_pkgname}")
conflicts=('openerp')
replaces=('openerp')
depends=(
    'gzip'
    'postgresql'
    'python2'
    'python2-argparse'
    'python2-babel'
    'python2-dateutil'
    'python2-docutils'
    'python2-decorator'
    'python2-egenix-mx-base'
    'python2-feedparser'
    'python2-gdata'
    'python2-gevent'
    'python2-ldap'
    'python2-lxml'
    'python2-mako'
    'python2-mock'
    'python2-jinja'
    'python2-openid'
    #'python2-openssl'
    'python2-passlib'
    'python2-paramiko'
    'python2-pillow'
    'python2-pip'
    'python2-psutil'
    'python2-psycopg2'
    'python2-pychart'
    'python2-pydot'
    'python2-pyparsing'
    'python2-pyusb'
    'python2-reportlab'
    'python2-pypdf'
    'python2-pytz'
    'python2-pywebdav'
    'python2-requests'
    'python2-simplejson'
    'python2-six'
    'python2-qrcode'
    'python2-unittest2'
    'python2-vatnumber'
    'python2-vobject'
    'python2-werkzeug'
    'python2-wsgiref'
    'python2-xlwt'
    'python2-yaml'
    'wkhtmltopdf-static'
    'zsi'
)
optdepends=(
    'antiword'
)

source=(
"http://nightly.odoo.com/8.0/nightly/src/${_pkgname}_${pkgver//_/.}.tar.gz"
odoo.confd
odoo.service
odoo.conf
)
backup=('etc/odoo/odoo.conf')
install=odoo.install

package()
{
  cd ${srcdir}/${_pkgname}-${pkgver//_/-}
  # Force package data inclusion
  sed -i -e s/#include_package_data/include_package_data/ setup.py
  python2 setup.py install --root="${pkgdir}"
  mkdir ${pkgdir}/etc/{conf.d,odoo} -p
  #mkdir ${pkgdir}/usr/share -p
  mkdir ${pkgdir}/usr/lib/systemd/system/ -p
  #mkdir ${pkgdir}/usr/share/man/{man1,man5} -p
  # Remove useless /usr/openerp directory
  #rm -rf ${pkgdir}/usr/openerp
  # Add server configs
  install -Dm 644 ${srcdir}/odoo.confd ${pkgdir}/etc/conf.d/odoo
  install -Dm 644 ${srcdir}/odoo.service ${pkgdir}/usr/lib/systemd/system/odoo.service
  install -Dm 644 ${srcdir}/odoo.conf ${pkgdir}/etc/odoo/odoo.conf
  # Not needed with wkhtmltopdf-static
  #install -Dm 755 ${srcdir}/wkhtmltopdf.sh ${pkgdir}/usr/local/bin/wkhtmltopdf
  #Install manpages
  #gzip -c openerp-server.1 > openerp-server.1.gz
  #gzip -c openerp_serverrc.5 > openerp_serverrc.5.gz
  #install -Dm 644  openerp-server.1.gz ${pkgdir}/usr/share/man/man1
  #install -Dm 644  openerp_serverrc.5.gz ${pkgdir}/usr/share/man/man5
}
md5sums=('1594516d5115f50a490671ed62364e40'
         '742fa9ad94a92ac2aa910197a26af4e8'
         '00314ef227c9075767d0165527de9841'
         '0c205f95168a60d140411cce4e173eb8')
