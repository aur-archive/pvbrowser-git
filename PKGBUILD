# Maintainer: Strigyskow

pkgname=pvbrowser-git
pkgver=20130807
pkgrel=3
pkgdesc="Process visualization, HMI and SCADA"
conflicts=pvbrowser
arch=('i686' 'x86_64')
url=('http://www.pvbrowser.org')
license=('GPL')
groups=()
depends=('qt5-base' 'qt5-webkit' 'qwt' 'python2' 'lua')
makedepends=('git')
#source=(pvb.tar.gz::http://pvbrowser.org/pvbrowser/download.php?file=pvb.tar.gz) # qmake-qt4.patch)
_gitrepo=(https://github.com/pvbrowser/pvb.git)
install='pvbrowser.install'
md5sums=('c299a271fe4ecb6e8992050e420de068')






build() {
  cd $srcdir
  if [ ! -d $srcdir/pvb ]; then
    git clone $_gitrepo
  else
    cd $srcdir/pvb
    git pull
  fi
  cd $srcdir/pvb
#  patch -p1 < $srcdir/qmake-qt4.patch
  ./build.sh
}

package() {
#  cd "$srcdir"/$pkgname-$pkgver
#  make prefix="$pkgdir"/usr install
#   $srcdir/pvb/install.sh

  install -d $pkgdir/srv/automation/shm
  install -d $pkgdir/srv/automation/mbx
  install -d $pkgdir/srv/automation/log
  chmod -R ugoa+rwx $pkgdir/srv/automation
  install -d  $pkgdir/opt/pvb
  install -d  $pkgdir/opt/pvb/doc
  install -d  $pkgdir/opt/pvb/pvsexample
  install -d  $pkgdir/opt/pvb/pvserver
  install -d  $pkgdir/opt/pvb/pvbrowser
  install -d  $pkgdir/opt/pvb/pvdevelop
  install -d  $pkgdir/opt/pvb/start_pvbapp
  install -d  $pkgdir/opt/pvb/designer/plugins
  install -d  $pkgdir/opt/pvb/rllib/lib
  install -d  $pkgdir/opt/pvb/rllib/rlsvg
  install -d  $pkgdir/opt/pvb/rllib/rlhistory
  install -d  $pkgdir/opt/pvb/fake_qmake
  install -d  $pkgdir/opt/pvb/language_bindings/lua/pvslua
  install -d  $pkgdir/opt/pvb/language_bindings/lua/pvapplua
  install -d  $pkgdir/opt/pvb/language_bindings/python/id
  install -d  $pkgdir/opt/pvb/language_bindings/python/mt
  install -d  $pkgdir/opt/pvb/language_bindings/python/template
  install -d  $pkgdir/opt/pvb/browserplugin
  install -d  $pkgdir/usr/lib
  install -d  $pkgdir/usr/bin

#  echo 'copy documentation...'
  cp -r $srcdir/pvb/doc $pkgdir/opt/pvb/
#  echo 'copy pvsexample...'
  cp -r $srcdir/pvb/pvsexample                                          $pkgdir/opt/pvb/
# Remove the binary of the example to avoid problems on 32 bit systems
  rm    $pkgdir/opt/pvb/pvsexample/pvsexample
# echo 'copy other files...'
  cp    $srcdir/pvb/LICENSE.GPL                                         $pkgdir/opt/pvb/
  cp    $srcdir/pvb/logo1.png                                           $pkgdir/opt/pvb/
  cp    $srcdir/pvb/custom.bmp                                          $pkgdir/opt/pvb/
  cp    $srcdir/pvb/gamsleiten.png                                      $pkgdir/opt/pvb/
  cp    $srcdir/pvb/pvbrowser.desktop                                   $pkgdir/opt/pvb/
  cp    $srcdir/pvb/pvdevelop.desktop                                   $pkgdir/opt/pvb/
  cp    $srcdir/pvb/pvserver/wthread.h                                  $pkgdir/opt/pvb/pvserver/
  cp    $srcdir/pvb/pvserver/BMP.h                                      $pkgdir/opt/pvb/pvserver/
  cp    $srcdir/pvb/pvserver/vmsglext.h                                 $pkgdir/opt/pvb/pvserver/
  cp    $srcdir/pvb/pvserver/pvbImage.h                                 $pkgdir/opt/pvb/pvserver/
  cp    $srcdir/pvb/pvserver/vmsgl.h                                    $pkgdir/opt/pvb/pvserver/
  cp    $srcdir/pvb/pvserver/processviewserver.h                        $pkgdir/opt/pvb/pvserver/
  cp    $srcdir/pvb/pvbrowser/pvbrowser                                 $pkgdir/opt/pvb/pvbrowser/
  cp    $srcdir/pvb/pvdevelop/pvdevelop                                 $pkgdir/opt/pvb/pvdevelop/
  cp    $srcdir/pvb/pvdevelop/pvdevelop.sh                              $pkgdir/opt/pvb/pvdevelop/
  cp    $srcdir/pvb/start_pvbapp/start_pvbapp                           $pkgdir/opt/pvb/start_pvbapp/
  cp    $srcdir/pvb/start_pvbapp/README.txt                             $pkgdir/opt/pvb/start_pvbapp/
  cp    $srcdir/pvb/start_pvbapp/example.ini.linux                      $pkgdir/opt/pvb/start_pvbapp/example.ini
  cp    $srcdir/pvb/start_pvbapp/start_if_not_already_running.sh        $pkgdir/opt/pvb/start_pvbapp/
  cp    $srcdir/pvb/rllib/rlsvg/rlsvgcat                                $pkgdir/opt/pvb/rllib/rlsvg/
  cp    $srcdir/pvb/rllib/rlhistory/rlhistory                           $pkgdir/opt/pvb/rllib/rlhistory/
  cp    $srcdir/pvb/fake_qmake/fake_qmake                               $pkgdir/opt/pvb/fake_qmake
  cp    $srcdir/pvb/rllib/lib/*.h                                       $pkgdir/opt/pvb/rllib/lib/
  cp    $srcdir/pvb/rllib/lib/nodave.o                                  $pkgdir/opt/pvb/rllib/lib/
  cp    $srcdir/pvb/rllib/lib/setport.o                                 $pkgdir/opt/pvb/rllib/lib/
  cp    $srcdir/pvb/language_bindings/lua/pvslua/pvslua                 $pkgdir/opt/pvb/language_bindings/lua/pvslua/
  cp    $srcdir/pvb/language_bindings/lua/pvapplua/pvapplua             $pkgdir/opt/pvb/language_bindings/lua/pvapplua/
# cp    $srcdir/pvb/language_bindings/README_PYTHON.txt                 $pkgdir/opt/pvb/language_bindings/
# cp    $srcdir/pvb/language_bindings/python/template/main.cpp          $pkgdir/opt/pvb/language_bindings/python/template/
# cp    $srcdir/pvb/language_bindings/python/template/Makefile          $pkgdir/opt/pvb/language_bindings/python/template/
# cp    $srcdir/pvb/language_bindings/python/template/mask1.cpp         $pkgdir/opt/pvb/language_bindings/python/template/
# cp    $srcdir/pvb/language_bindings/python/template/mask1.py          $pkgdir/opt/pvb/language_bindings/python/template/
# cp    $srcdir/pvb/language_bindings/python/template/mask1_slots.h     $pkgdir/opt/pvb/language_bindings/python/template/
# cp    $srcdir/pvb/language_bindings/python/template/pvapp.h           $pkgdir/opt/pvb/language_bindings/python/template/
# cp    $srcdir/pvb/language_bindings/python/template/pvs_init.py       $pkgdir/opt/pvb/language_bindings/python/template/
# cp    $srcdir/pvb/language_bindings/python/template/pvs.pro           $pkgdir/opt/pvb/language_bindings/python/template/
# cp    $srcdir/pvb/language_bindings/python/template/pvs.pvproject     $pkgdir/opt/pvb/language_bindings/python/template/
  cp    $srcdir/pvb/designer/README.txt                                 $pkgdir/opt/pvb/designer/
  cp    $srcdir/pvb/browserplugin/pvbrowserplugin-example.html          $pkgdir/opt/pvb/browserplugin/
  cp    $srcdir/pvb/browserplugin/README.txt                            $pkgdir/opt/pvb/browserplugin/
  cp    $srcdir/pvb/browserplugin/libpvbrowser.so                       $pkgdir/opt/pvb/browserplugin/
  cp    $srcdir/pvb/language_bindings/python/mt/pv.py                   $pkgdir/opt/pvb/language_bindings/python/mt/
  cp    $srcdir/pvb/language_bindings/python/mt/_pv.so                  $pkgdir/opt/pvb/language_bindings/python/mt/
  cp    $srcdir/pvb/language_bindings/python/mt/rllib.py                $pkgdir/opt/pvb/language_bindings/python/mt/
  cp    $srcdir/pvb/language_bindings/python/mt/_rllib.so               $pkgdir/opt/pvb/language_bindings/python/mt/
  cp    $srcdir/pvb/language_bindings/python/id/pv.py                   $pkgdir/opt/pvb/language_bindings/python/id/
  cp    $srcdir/pvb/language_bindings/python/id/_pv.so                  $pkgdir/opt/pvb/language_bindings/python/id/
  cp    $srcdir/pvb/language_bindings/python/id/rllib.py                $pkgdir/opt/pvb/language_bindings/python/id/
  cp    $srcdir/pvb/language_bindings/python/id/_rllib.so               $pkgdir/opt/pvb/language_bindings/python/id/
  cp    $srcdir/pvb/designer/plugins/libpvb_designer_plugin.so          $pkgdir/opt/pvb/designer/plugins/
#  cp    $srcdir/pvb/designer/plugins/libqwt_designer_plugin.so          $pkgdir/opt/pvb/designer/plugins/
  cp    $srcdir/pvb/qwt/designer/plugins/designer/libqwt_designer_plugin.so $pkgdir/opt/pvb/designer/plugins/
  cp    $srcdir/pvb/pvserver/libpvsid.so                                $pkgdir/opt/pvb/pvserver/
  cp    $srcdir/pvb/pvserver/libpvsmt.so                                $pkgdir/opt/pvb/pvserver/
  cp    $srcdir/pvb/pvserver/libpvsid.a                                 $pkgdir/opt/pvb/pvserver/
  cp    $srcdir/pvb/pvserver/libpvsmt.a                                 $pkgdir/opt/pvb/pvserver/
  cp    $srcdir/pvb/rllib/lib/librllib.so                               $pkgdir/opt/pvb/rllib/lib/

  ln -sf /opt/pvb/pvbrowser/pvbrowser                     	$pkgdir/usr/bin/pvbrowser
  cp $pkgdir/opt/pvb/pvdevelop/pvdevelop.sh                      	$pkgdir/usr/bin/pvdevelop
  ln -sf /opt/pvb/rllib/rlsvg/rlsvgcat                    	$pkgdir/usr/bin/rlsvgcat
  ln -sf /opt/pvb/rllib/rlsvg/rlsvgcat                    	$pkgdir/usr/bin/rlsvgcat
  ln -sf /opt/pvb/start_pvbapp/start_pvbapp               	$pkgdir/usr/bin/start_pvbapp
  ln -sf /opt/pvb/rllib/rlhistory/rlhistory               	$pkgdir/usr/bin/rlhistory
  ln -sf /opt/pvb/fake_qmake/fake_qmake                   	$pkgdir/usr/bin/fake_qmake
  ln -sf /opt/pvb/update_pvbrowser.sh                     	$pkgdir/usr/bin/update_pvbrowser
  ln -sf /opt/pvb/language_bindings/lua/pvslua/pvslua     	$pkgdir/usr/bin/pvslua
  ln -sf /opt/pvb/language_bindings/lua/pvapplua/pvapplua 	$pkgdir/usr/bin/pvapplua
  
  ln -sf /opt/pvb/rllib/lib/librllib.so         		$pkgdir/usr/lib/librllib.so
  ln -sf /opt/pvb/rllib/lib/librllib.so         		$pkgdir/usr/lib/librllib.so.1
  ln -sf /opt/pvb/rllib/lib/librllib.so         		$pkgdir/usr/lib/librllib.so.1.0
  ln -sf /opt/pvb/rllib/lib/librllib.so         		$pkgdir/usr/lib/librllib.so.1.0.0
  
  ln -sf /opt/pvb/pvserver/libpvsid.so          		$pkgdir/usr/lib/libpvsid.so
  ln -sf /opt/pvb/pvserver/libpvsid.so          		$pkgdir/usr/lib/libpvsid.so.1
  ln -sf /opt/pvb/pvserver/libpvsid.so          		$pkgdir/usr/lib/libpvsid.so.1.0
  ln -sf /opt/pvb/pvserver/libpvsid.so          		$pkgdir/usr/lib/libpvsid.so.1.0.0
  
  ln -sf /opt/pvb/pvserver/libpvsmt.so          		$pkgdir/usr/lib/libpvsmt.so
  ln -sf /opt/pvb/pvserver/libpvsmt.so          		$pkgdir/usr/lib/libpvsmt.so.1
  ln -sf /opt/pvb/pvserver/libpvsmt.so          		$pkgdir/usr/lib/libpvsmt.so.1.0
  ln -sf /opt/pvb/pvserver/libpvsmt.so          		$pkgdir/usr/lib/libpvsmt.so.1.0.0

#  echo 'making /opt/pvb/pvsexample writeable...'
  chmod ugoa+w $pkgdir/opt/pvb/pvsexample
  chmod ugoa+w $pkgdir/opt/pvb/pvsexample/*

  #copy qt designer plugins to destination
#  install -d   $pkgdir/usr/lib/qt/plugins/designer
#  install      $pkgdir/opt/pvb/designer/plugins/* 			$pkgdir/usr/lib/qt/plugins/designer

  #copy application files
  install -d $pkgdir/usr/share/applications
  install $pkgdir/opt/pvb/*.desktop   					$pkgdir/usr/share/applications

}
