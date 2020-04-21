## <center>Un-Official Gojek API Wrapper</center>
Repository Berikut Ini Merupakan Porting Dari [GOJEK](https://github.com/ridwanfathin/gojek) Untuk PHP

<b>Fitur Akun Pengguna GOJEK</b>
- [x] Login Dengan Nomor Handphone Untuk Mendapatkan `loginToken`
- [x] Login Dengan Email Untuk Mendapatkan `loginToken`
- [x] Login Dengan OTP Untuk Mendapatkan `authToken`
- [x] Menampilkan Informasi Akun Pengguna
- [x] Melakukan Perubahan Pada Akun
- [ ] Melakukan Verifikasi Perubahan Pada Akun
- [x] Menampilkan Jumlah Saldo
- [x] Logout

<b>Fitur Akun Pengguna GOPAY</b>
- [x] Menampilkan Detail Data Informasi
- [x] Menampilkan History Transaksi
- [x] Mengambil Data Wallet Code `QrId` Untuk Method Transfer
- [x] Transfer Ke Sesama GOPAY

<b>Fitur Data Booking GOJEK</b>
- [ ] Menampilkan Booking History
- [ ] Menampilkan Booking Yang Masih Aktif
- [ ] Mengambil Data Booking Berdasarkan `orderNo`
- [ ] Mengkalkulasi Pemakaian GOPAY Pada GOJEK

<b>Fitur Data GOFOOD</b>
- [ ] Menampilkan Data GOFOOD Bedasarkan Lokasi `latLong`
- [ ] Menampilkan Data GOFOOD Bedasarkan Lokasi `latLong` Dan `limit`
- [ ] Menampilkan Data Restaurant Bedasarkan `restaurantId`
- [ ] Menampilkan Data Restaurant Bedasarkan `category`

<b>Fitur Data GOPOINTS</b>
- [ ] Menampilkan Jumlah Point
- [ ] Menampilkan Point Lanjutan
- [ ] Menebus Point

<b>Fitur Data Area GORIDE GOCAR GOSEND</b>
- [ ] Menampilkan Data Area Semua Driver Terdekat Berdasarkan Lokasi `latLong`
- [ ] Menampilkan Data Area Driver Terdekat GORIDE Berdasarkan Lokasi `latLong`
- [ ] Menampilkan Data Area Driver Terdekat GOCAR Berdasarkan Lokasi `latLong`
- [ ] Menampilkan Data Area Driver Terdekat GOSEND Berdasarkan Lokasi `latLong`

<b>Fitur Data Area GOMART</b>
- [ ] Menampilkan Data Area Terdekat Berdasarkan Lokasi `latLong`

### Dokumentasi

#### Langkah Untuk Menjalankan GojekID
##### Ambil Paket Pada Composer
```php
composer require maulana20/gojekid
```
##### Jika Di Jalankan Dengan Laravel Tinker

[![tinker](./screen/tinker.PNG)](./../../)

##### Jika Di Jalankan Dengan Native
```php
require 'vendor/autoload.php';
use Maulana20\GojekID;

$gojek = new GojekID();
```

#### Fitur Akun Pengguna GOJEK
##### Login Dengan Nomor Handphone
```php
$loginToken = $gojek->loginPhone('<mobilePhone>')->getLoginToken();
```
##### Login Dengan Email
```php
$loginToken = $gojek->loginEmail('<Email>')->getLoginToken();
```
##### Login Pada GOJEK
```php
$authToken = $gojek->loginGojek('<loginToken>', '<OTP>')->getAuthToken();
```
##### Menampilkan Informasi Akun Pengguna
```php
$gojek->setAuthToken('<authToken>');
$result = $gojek->getCustomer()->getResult();
```
##### Melakukan Perubahan Pada Akun
```php
$gojek->setAuthToken('<authToken>');
$result = $gojek->editAccount('<mobilePhone>', '<email>', '<name>')->getResult();
```
##### Melakukan Verifikasi Perubahan Pada Akun
```php
$gojek->setAuthToken('<authToken>');
$result = $gojek->editAccountVerify('<id>', '<mobilePhone>', '<verificationCode>')->getResult();
```
##### Menampilkan Jumlah Saldo
```php
$gojek->setAuthToken('<authToken>');
$balance = $gojek->checkBalance()->getBalance();
```
##### Logout
```php
$gojek->setAuthToken('<authToken>');
$gojek->logout();
```

#### Fitur Akun Pengguna GOPAY
##### Menampilkan Detail Data Informasi
```php
$gojek->setAuthToken('<authToken>');
$result = $gojek->gopayDetail()->getResult();
```
##### Menampilkan History Transaksi
```php
$gojek->setAuthToken('<authToken>');
$result = $gojek->gopayHistory('<page>', '<limit>')->getResult();
```
##### Mengambil Data Wallet Code
```php
$gojek->setAuthToken('<authToken>');
$QrId = $gojek->checkWalletCode('<mobilePhoneTo>')->getQrId();
```
##### Transfer Ke Sesama GOPAY
```php
$gojek->setAuthToken('<authToken>');
$ref = $gojek->gopayTransfer('<QrId>', '<PIN>', '<amount>', '<description>')->getRef();
```

### Melakukan Testing Pada PHP Unit Tests

[![php-test](./screen/php-test.PNG)](./../../)

### Author

[Maulana Saputra](mailto:maulanasaputra11091082@gmail.com)
