# Maintainer: Your Name <your.email@example.com>
pkgname=water-temp-sensor
pkgver=0.0.1
pkgrel=1
pkgdesc="Water temperature sensor service for reading temperature from serial device"
arch=('any')
url="https://github.com/radumarinoiu/water-temp-sensor.git"
license=('GPL-3.0-or-later')
depends=('python' 'python-pyserial')
source=("water-temp-sensor" "water-temp-sensor.service" "water-temp-sensor.conf")
sha256sums=('929d30e00afcb02094d5613734821ae57303ff2a75a8fcd4e9208262fa2128f2'
            'd13c42078ae1a6bb5e3c4503e4b920b6415966edcb8dd096c37107f66ed235c9'
            '4dd5a2880e2a34bbf797262b92f37796c089e2663e770ac71351532d3e559319')

package() {
  # Install the main script
  install -Dm755 "$srcdir/water-temp-sensor" "$pkgdir/usr/bin/water-temp-sensor"
  
  # Install systemd service file
  install -Dm644 "$srcdir/water-temp-sensor.service" "$pkgdir/usr/lib/systemd/system/water-temp-sensor.service"
  
  # Install config file
  install -Dm644 "$srcdir/water-temp-sensor.conf" "$pkgdir/etc/water-temp-sensor.conf"
}
