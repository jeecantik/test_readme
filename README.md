###### Nama: Jenissa ananda yoanita
###### Kelas: Rpl
###### No. Absen: 31

# Modul 1

Soal Nomor 1
Lakukan proses instalasi framework laravel kedalam folder dengan nama masing-masing 

```
composer create-project laravel/laravel penjualan
```


# Modul 2 

###### Soal Nomor 1
Buatlah migration table kategori dengan menggunakan teknik yang telah dipelajari dalam modul ini.

##### Langkah pertama
membuat table dengan migration menggunakan perintah dibawah ini di terminal : 
```
php artisan make:migration create_produk_table>
```

##### langkah kedua 
isikan kode dibawah ini kedalam file yang dibuat  didalam folder
```
2022_07_25_072255_create_kategori_tabel
```
Isikan kode didalam folder tersebut seperti ini :
```
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('kategori',function (Blueprint $table) {
            $table->id();
            $table->string('nama');
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::dropIfExists('kategori');
    }
};
```
###### langkah ketiga 
lalu membuat Model dengan menggunakan script berikut ini kedalam terminal :
```
php artisan make:model kategori
```
maka akan terjadi folder
```
kategori.php
```
Jika sudah jadi maka isi seperti dibawah ini : 
```
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class kategori extends Model
{
    use HasFactory;

    protected $table = 'kategori';
}

``` 

###### langkah keempat 
untuk menghapus tabel, kita dapat menjalankan perintah berikut :
```
php artisan migrate:rollback
```
perintah artisan tersebut akan atau mengembalikan satu operasi atu operasi terkhir yang telah dilakukan 
kita juga dapat rollback seluruh operasi migration, yaitu dengan perintah:
```
php artisan migrate:reset
```
atau kita ingin me rollback seluruh operasi migration dan langsung menjalankan migration 
```
php artisan migrate:refresh
```
###### Soal Nomor 2
Seeder digunakan untuk membuat contoh data pada database.Sangat bermanfaat saat melakakukan pengembangan suatu sistem yang dimana kita memerlukan suatu contoh data.Apalagi ketik untuk membutuhkan contoh data yang banyak, dapat membantu daripada memasukkan data satu persatu secara manual memaluliPhpMyAdmin. Untuk membuat seeder gunakan perintah diibawah ini didalam terminal: 
```
php artisan make:seeder kategoriTableSeeder
```
lalu akan meghasilkan satu file pada folder database/seeder dengan nama:
```
kategoriTableSeeder.php
```
Selanjutnya buka file seeder kategoriTableSeeder lalu isi seperti ini:
```
<?php

namespace Database\Seeders;

use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;
use DB;

class kategoriTableSeeder extends Seeder
{
    /**
     * Run the database seeds.
     *
     * @return void
     */
    public function run()
    {
        DB::table('kategori')->insert(array(
            [
                'nama' => 'Perlengkapan sekolah',
            ],
            [
                'nama' => 'Komputer',
            ],
            [
                'nama' => 'Sabun',
            ],
            [
                'nama' => 'Accesories',
            ],
            [
                'nama' => 'ATK',
            ]
            
        ));   
    }
}
```
langkah terkahir buka file <DatabaseSeedeer.php> dan panggil seeder yang baru dibuat:
```
<?php

namespace Database\Seeders;

// use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;

class DatabaseSeeder extends Seeder
{
    /**
     * Seed the application's database.
     *
     * @return void
     */
    public function run()
    {
        $this->call(produkTableSeeder::class);
        $this->call(kategoriTableSeeder::class);
    }
}
```
Sekarang kita bisa lakukan perintah ini untuk mengeksekusi seeder yang dibuat: 
```
php artisan db:seed
```
