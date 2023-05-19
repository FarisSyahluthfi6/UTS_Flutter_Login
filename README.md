
| Nama      | Faris Syahluthfi |
| ----------- | ----------- |
| NIM     | 312010034       |
| Kelas   | TI.20.A.1        |

![output](screenshot/faris.jpg)</p>

## Membuat Tampilan Login, Registrasi dan Lupa Password Menggunakan Flutter Dart. </p></br>
# 1. Download Flutter</p>
<li> Download SDK Flutternya di: https://docs.flutter.dev/get-started/install . </li> </p>
<li> Pilih operasi sistem sesuai laptop atau PC kalian, disini saya pake sistem operasi windows. Jadi saya download Flutternya Windows.</li></p> </br>

# 2. Installasi Flutter di Windows

<li> Ekstak file Flutter yang sudah di download. Caranya adalah klik kanan, pilih ekstak here, setelah itu tunggu sampai ekstak selesai. </li><p>
<li> Pindahkan file Flutter yang sudah di ekstak ke dalam disk C atau disk D. Disini saya memindahkannya ke disk C.

![flutter](screenshot/flutter.png)</li></p>

<li> Pilih menu pencarian di bawah. contoh environment di windows:

![enviroment](screenshot/enviroment.png)</li></p>
<li> pilih environment variable

![enviroment](screenshot/enviroment2.png)</li></p>

<li> pilih path

![enviroment](screenshot/enviroment3.png)</li></p>

<li> new lalu arahkan ke file flutternya

![enviroment](screenshot/enviroment4.png)</li></p></br>

# 3. Membuat Projek Aplikasinya </br>

<li> Kita akan membuat program aplikasinya di Visual Studio Code. Buka aplikasi Visual Studio Code

![vscode](screenshot/vscode.png)</li></p></br>

<li> Pilih menu <b> Ekstensions </b> sebelah kiri untuk menginstal <b> FLUTTER dan DART </b>

![ekstension](screenshot/ekstension1.png)</li></p></br>

![ekstension](screenshot/ekstension2.png)</li></p></br>

![ekstension](screenshot/ekstension3.png)</li></p></br>

<li> Klik fn+f2 untuk membuat folder baru flutter

![vscode](screenshot/vscode1.png)</li></p></br>

<li> inilah penampakannya jika kalian berhasil

![vscode](screenshot/vscode2.png)</li></p></br>

# 4. Membuat Screen Login Flutter Dart </p></br>
<li> Buat folder baru <b>assets</b>, kemudian cari background untuk Login dan Register.</li></p></br>

![assets](screenshot/assets.png)</li></p></br>

<li> Buka file <b> pubspec.yaml </b> Lalu buat code berikut:

![pubspec](screenshot/pubspec.png)</li></p></br>

```java
flutter:
  assets:
    - assets/login.jpg
    - assets/register.jpg

```
 </li></p></br>
Penjelasan codingan: Fungsi code diatas adalah untuk menampilkan gambar atau background kedalam flutter. </li></p></br>

<li> Di folder <b>lib<b>, Buat file baru dengan nama <b>login.dart<b>, Kemudian isikan codingan berikut:

```java

import 'package:flutter/material.dart';

class MyLogin extends StatefulWidget {
  const MyLogin({Key? key}) : super(key: key);

  @override
  _MyLoginState createState() => _MyLoginState();
}

class _MyLoginState extends State<MyLogin> {
  //Password Field obscureText  Handler
  bool _isHidden = true;
  void _toggleVisibility() {
    setState(() {
      _isHidden = !_isHidden;
    });
  }

  @override
  Widget build(BuildContext context) {
    return SafeArea(
      child: Container(
        decoration: BoxDecoration(
          image: DecorationImage(
            image: AssetImage(
              'assets/login.jpg',
            ),
            fit: BoxFit.cover,
          ),
        ),
        child: Scaffold(
          backgroundColor: Color.fromARGB(0, 0, 0, 0),
          body: Stack(
            children: [
              Row(
                mainAxisAlignment: MainAxisAlignment.center,
                children: [
                  Container(
                    padding: EdgeInsets.only(
                      top: 50.0,
                    ),
                    child: Text(
                      '\n LOGIN',
                      textAlign: TextAlign.left,
                      style: TextStyle(
                        color: Color.fromARGB(255, 233, 231, 231),
                        fontSize: 55.0,
                      ),
                    ),
                  ),
                ],
              ),
              SingleChildScrollView(
                child: Container(
                  padding: EdgeInsets.only(
                    top: MediaQuery.of(context).size.height * 0.5,
                    left: 35,
                    right: 35,
                  ),
                  child: Column(
                    children: [
                      TextField(
                        decoration: InputDecoration(
                          labelText: 'Email',
                          prefixIcon: Icon(Icons.email_outlined),
                          fillColor: Color.fromARGB(234, 237, 251, 253),
                          filled: true,
                          border: OutlineInputBorder(
                            borderRadius: BorderRadius.circular(10.0),
                          ),
                        ),
                      ),
                      SizedBox(height: 30.0),
                      TextFormField(
                        validator: (value) {
                          if (value == null || value.isEmpty) {
                            return 'Please enter the password';
                          } else if (value.length <= 6) {
                            return 'Password must be greater than 6 digits';
                          }
                          return null;
                        },
                        obscureText: true,
                        decoration: InputDecoration(
                          labelText: 'Password',
                          fillColor: Color.fromARGB(234, 237, 251, 253),
                          prefixIcon: Icon(Icons.lock),
                          suffixIcon: IconButton(
                            onPressed: _toggleVisibility,
                            icon: _isHidden
                                ? Icon(Icons.visibility)
                                : Icon(Icons.visibility_off),
                          ),
                          filled: true,
                          // hintText: 'Password',
                          border: OutlineInputBorder(
                            borderRadius: BorderRadius.circular(10.0),
                          ),
                        ),
                      ),
                      SizedBox(height: 30.0),
                      Row(
                        mainAxisAlignment: MainAxisAlignment.end,
                        children: [
                          ElevatedButton(
                              style: ElevatedButton.styleFrom(
                                maximumSize: Size(170.0, 90.0),
                                minimumSize: Size(170.0, 60.0),
                                primary: Color.fromARGB(255, 180, 21, 9),
                                shape: StadiumBorder(),
                              ),
                              onPressed: () {},
                              child: Row(
                                mainAxisAlignment:
                                    MainAxisAlignment.spaceBetween,
                                //crossAxisAlignment: CrossAxisAlignment.center,
                                children: [
                                  Text('LOG IN'),
                                  Icon(
                                    Icons.lock,
                                    color: Colors.white,
                                  ),
                                ],
                              )),
                        ],
                      ),
                      SizedBox(height: 35.0),
                      Row(
                        mainAxisAlignment: MainAxisAlignment.spaceBetween,
                        children: [
                          TextButton(
                            onPressed: () {
                              Navigator.pushNamed(context, 'register');
                            },
                            child: Text(
                              'Create an Account',
                              style: TextStyle(
                                  color: Color.fromARGB(255, 180, 21, 9),
                                  fontSize: 17,
                                  fontWeight: FontWeight.bold,
                                  decorationThickness: 2),
                            ),
                          ),
                          TextButton(
                            onPressed: () {
                              Navigator.pushNamed(context, 'forgot');
                            },
                            child: Text(
                              'Forgot Password?',
                              style: TextStyle(
                                  color: const Color.fromARGB(255, 180, 21, 9),
                                  fontSize: 17,
                                  fontWeight: FontWeight.bold,
                                  decorationThickness: 2),
                            ),
                          ),
                        ],
                      ),
                    ],
                  ),
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }
}


```
</li></p></br>
Penjelasan dari codingan di atas:</p>
1. import 'package:flutter/material.dart';: Mengimpor package flutter/material.dart, yang berisi kelas-kelas yang digunakan untuk membangun antarmuka pengguna (UI) dengan menggunakan framework Flutter. </p>
2. import 'package:flutter_application_1/login.dart';: Mengimpor file login.dart yang berisi kode untuk halaman login. </p>
3. import 'package:flutter_application_1/register.dart';: Mengimpor file register.dart yang berisi kode untuk halaman registrasi.</p>
4. import 'package:flutter_application_1/resetpass.dart';: Mengimpor file resetpass.dart yang berisi kode untuk halaman reset password.</p>
5. void main() { ... }: Ini adalah fungsi utama yang akan dijalankan saat aplikasi dijalankan. Fungsi ini akan menjalankan aplikasi Flutter.</p>
6. runApp(...);: Metode runApp adalah metode yang digunakan untuk menjalankan aplikasi Flutter. Di dalamnya, kita memberikan MaterialApp sebagai widget utama.</p>
7. MaterialApp: Ini adalah widget yang membangun dan mengkonfigurasi aplikasi Flutter. Widget ini memiliki beberapa properti seperti debugShowCheckedModeBanner, initialRoute, title, dan routes.</p>
8. debugShowCheckedModeBanner: false,: Properti ini digunakan untuk menghilangkan tanda "Debug" pada aplikasi.</p>
9. initialRoute: 'login',: Properti ini menentukan rute awal aplikasi, dalam hal ini adalah halaman login.</p>
10. title: 'LOGIN',: Properti ini digunakan untuk memberikan judul pada aplikasi.</p>
11. routes: { ... }: Properti ini digunakan untuk mendefinisikan rute-rute yang ada dalam aplikasi. Setiap rute memiliki nama yang unik dan dihubungkan dengan widget yang akan ditampilkan.</p>
12. 'login': (context) => MyLogin(),: Ini adalah definisi rute untuk halaman login. Ketika rute ini dipanggil, widget MyLogin akan ditampilkan.</p>
13. 'register': (context) => myRegister(),: Ini adalah definisi rute untuk halaman registrasi. Ketika rute ini dipanggil, widget myRegister akan ditampilkan.</p>
14. 'forgot': (context) => resetPassword(),: Ini adalah definisi rute untuk halaman reset password. Ketika rute ini dipanggil, widget resetPassword akan ditampilkan.</p>

<li>Selanjutnya, buka file <b>main.dart</b> hapus semua codingannya, lalu ketik kodingan baru berikut ini:</p></br>

```java

import 'package:flutter/material.dart'; 
import 'package:flutter_application_1/login.dart';
import 'package:flutter_application_1/register.dart';
import 'package:flutter_application_1/resetpass.dart';

void main() {
  runApp(
    MaterialApp(
      debugShowCheckedModeBanner: false,
      initialRoute: 'login',
      title: 'LOGIN',
      routes: {
        'login': (context) => MyLogin(),
        'register': (context) => myRegister(),
        'forgot': (context) => resetPassword(),
      },
    ),
  );
}


```
</p></br>

Penjelasan codingan di atas: </p>
1.`import 'package:flutter/material.dart';`: Mengimpor package `flutter/material.dart`, yang berisi kelas-kelas yang diperlukan untuk membangun antarmuka pengguna (UI) menggunakan framework Flutter.</p>

2.`import 'package:flutter_application_1/login.dart';`: Mengimpor file `login.dart` yang berisi kode untuk halaman login. File ini kemungkinan berisi definisi dari kelas `MyLogin` yang merupakan widget untuk tampilan halaman login.</p>

3.`import 'package:flutter_application_1/register.dart';`: Mengimpor file `register.dart` yang berisi kode untuk halaman registrasi. File ini kemungkinan berisi definisi dari kelas `myRegister` yang merupakan widget untuk tampilan halaman registrasi.</p>

4.`import 'package:flutter_application_1/resetpass.dart';`: Mengimpor file `resetpass.dart` yang berisi kode untuk halaman reset password. File ini kemungkinan berisi definisi dari kelas `resetPassword` yang merupakan widget untuk tampilan halaman reset password.</p>

5.`void main() { ... }`: Ini adalah fungsi utama yang akan dijalankan saat aplikasi dijalankan. Fungsi ini akan menjalankan aplikasi Flutter.</p>

6.`runApp(...);`: Metode `runApp` digunakan untuk menjalankan aplikasi Flutter. Di dalamnya, kita memberikan `MaterialApp` sebagai widget utama.</p>

7.`MaterialApp`: Ini adalah widget yang membangun dan mengkonfigurasi aplikasi Flutter. Widget ini memiliki beberapa properti seperti `debugShowCheckedModeBanner`, `initialRoute`, `title`, dan `routes`.</p>

8.`debugShowCheckedModeBanner: false,`: Properti ini digunakan untuk menghilangkan tanda "Debug" pada aplikasi.</p>

9.`initialRoute: 'login',`: Properti ini menentukan rute awal aplikasi, dalam hal ini adalah halaman login.</p>

10.`title: 'LOGIN',`: Properti ini digunakan untuk memberikan judul pada aplikasi.</p>

11.`routes: { ... }`: Properti ini digunakan untuk mendefinisikan rute-rute yang ada dalam aplikasi. Setiap rute memiliki nama yang unik dan dihubungkan dengan widget yang akan ditampilkan.</p>

12.`'login': (context) => MyLogin(),`: Ini adalah definisi rute untuk halaman login. Ketika rute ini dipanggil, widget `MyLogin` akan ditampilkan.</p>

13.`'register': (context) => myRegister(),`: Ini adalah definisi rute untuk halaman registrasi. Ketika rute ini dipanggil, widget `myRegister` akan ditampilkan.</p>

14.`'forgot': (context) => resetPassword(),`: Ini adalah definisi rute untuk halaman reset password. Ketika rute ini dipanggil, widget `resetPassword` akan ditampilkan.</p></br>

# 5. Membuat Screen Registrasi Flutter Dart </p></br>
Langkah selanjutnya adalah membuat Screen Registrasi, caranya adalah sebagai berikut: </p>

<li> Buat File baru di Folder <b>lib</b> kita beri nama filenya yaitu <b>register.dart</b>, Kemudian kita ketik codingan di dalam file tersebut. Berikut ini codingannya: </p></br>

```java

import 'package:flutter/material.dart';

class myRegister extends StatefulWidget {
  const myRegister({Key? key}) : super(key: key);

  @override
  _myRegisterState createState() => _myRegisterState();
}

class _myRegisterState extends State<myRegister> {
  //Password Field obscureText  Handler
  bool _isHidden = true;
  void _toggleVisibility() {
    setState(() {
      _isHidden = !_isHidden;
    });
  }

  @override
  Widget build(BuildContext context) {
    return SafeArea(
      child: Container(
        decoration: BoxDecoration(
          image: DecorationImage(
            image: AssetImage(
              'assets/register.jpg',
            ),
            fit: BoxFit.cover,
          ),
        ),
        child: Scaffold(
          appBar: AppBar(
              elevation: null,
              backgroundColor: Colors.white,
              leading: TextButton(
                onPressed: () {
                  Navigator.pushNamed(context, 'login');
                },
                child: Icon(
                  Icons.arrow_back_ios_rounded,
                  color: Colors.white,
                ),
              )),
          backgroundColor: Color.fromARGB(0, 168, 122, 122),
          body: Stack(
            children: [
              Row(
                mainAxisAlignment: MainAxisAlignment.center,
                children: [
                  Text(
                    'REGISTER',
                    textAlign: TextAlign.center,
                    style: TextStyle(
                      color: Colors.white,
                      fontSize: 35.0,
                    ),
                  ),
                ],
              ),
              SingleChildScrollView(
                child: Container(
                  padding: EdgeInsets.only(
                    top: MediaQuery.of(context).size.height * 0.25,
                    left: 30,
                    right: 30,
                  ),
                  child: Column(
                    children: [
                      TextField(
                        style: TextStyle(
                          color: Colors.white,
                        ),
                        decoration: InputDecoration(
                          labelText: 'Username',
                          fillColor: Color.fromARGB(255, 54, 55, 56),
                          filled: true,
                          border: OutlineInputBorder(
                              borderRadius: BorderRadius.circular(10.0),
                              borderSide: const BorderSide(
                                color: Color.fromARGB(255, 255, 255, 255),
                              )),
                              labelStyle: TextStyle(
                            color: const Color.fromARGB(255, 255, 255, 255),
                          ),
                        ),
                      ),
                      SizedBox(height: 30.0),
                      TextField(
                        style: TextStyle(
                          color: Colors.white,
                        ),
                        decoration: InputDecoration(
                          fillColor: Color.fromARGB(255, 54, 55, 56),
                          prefixIcon: Icon(Icons.email_outlined),
                          filled: true,
                          labelText: 'Email',
                          border: OutlineInputBorder(
                            borderRadius: BorderRadius.circular(10.0),
                            borderSide: BorderSide(
                              color: Color.fromARGB(255, 255, 255, 255),
                            ),
                          ),
                          labelStyle: TextStyle(
                            color: const Color.fromARGB(255, 255, 255, 255),
                          ),
                        ),
                      ),
                      SizedBox(height: 30.0),
                      TextField(
                        style: TextStyle(
                          color: Colors.white,
                        ),
                        decoration: InputDecoration(
                          fillColor: Color.fromARGB(255, 54, 55, 56),
                          prefixIcon: Icon(Icons.phone),
                          filled: true,
                          labelText: 'Phone',
                          border: OutlineInputBorder(
                            borderRadius: BorderRadius.circular(10.0),
                            borderSide: const BorderSide(
                              color: Color.fromARGB(255, 255, 255, 255),
                            ),
                          ),
                          labelStyle: TextStyle(
                            color: const Color.fromARGB(255, 255, 255, 255),
                          ),
                        ),
                      ),
                      SizedBox(height: 30.0),
                      TextField(
                        style: TextStyle(
                          color: Colors.white,
                        ),
                        obscureText: _isHidden,
                        decoration: InputDecoration(
                          fillColor: Color.fromARGB(255, 27, 27, 27),
                          prefixIcon: Icon(Icons.lock),
                          suffixIcon: IconButton(
                            onPressed: _toggleVisibility,
                            icon: _isHidden
                                ? Icon(Icons.visibility)
                                : Icon(Icons.visibility_off),
                          ),
                          labelText: 'Password',
                          filled: true,
                          border: OutlineInputBorder(
                            borderRadius: BorderRadius.circular(10.0),
                            borderSide: const BorderSide(
                              color: Color.fromARGB(255, 255, 255, 255),
                            ),
                          ),
                          labelStyle: TextStyle(
                            color: const Color.fromARGB(255, 255, 255, 255),
                          ),
                        ),
                      ),
                      SizedBox(height: 30.0),
                      Row(
                        mainAxisAlignment: MainAxisAlignment.end,
                        children: [
                          ElevatedButton(
                              style: ElevatedButton.styleFrom(
                                maximumSize: const Size(170.0, 90.0),
                                minimumSize: const Size(170.0, 60.0),
                                primary: Colors.black,
                                shape: const StadiumBorder(),
                              ),
                              onPressed: () {},
                              child: Row(
                                mainAxisAlignment:
                                    MainAxisAlignment.spaceBetween,
                                //crossAxisAlignment: CrossAxisAlignment.center,
                                children: [
                                  Text('REGISTER'),
                                  Icon(
                                    Icons.content_paste_rounded,
                                    color: Colors.white,
                                  ),
                                ],
                              )),
                        ],
                      ),
                      SizedBox(height: 30.0),
                      Row(
                        mainAxisAlignment: MainAxisAlignment.spaceBetween,
                        children: [
                          TextButton(
                            onPressed: () {
                              Navigator.pushNamed(context, 'login');
                            },
                            child: Text(
                              'Login',
                              style: TextStyle(
                                  color: Color.fromARGB(255, 243, 239, 239)),
                            ),
                          ),
                          TextButton(
                            onPressed: () {
                              Navigator.pushNamed(context, 'forgot');
                            },
                            child: Text(
                              'Forgot password?',
                              style: TextStyle(color: Colors.white),
                            ),
                          ),
                        ],
                      ),
                    ],
                  ),
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }
}

```
</p></br>

Berikut ini adalah penjelasan dari codingan diatas: </p></br>

1. `class myRegister extends StatefulWidget { ... }`: Mendefinisikan kelas `myRegister` yang merupakan turunan dari `StatefulWidget`. `StatefulWidget` digunakan ketika widget memiliki state yang berubah selama masa hidupnya.</p>

2. `const myRegister({Key? key}) : super(key: key);`: Konstruktor untuk kelas `myRegister`. Ini menerima parameter `key` yang diperlukan oleh `StatefulWidget` superclass.</p>

3. `_myRegisterState createState() => _myRegisterState();`: Membuat instance dari `_myRegisterState` yang merupakan subclass dari `State` untuk mengatur state dari widget `myRegister`.</p>

4. `class _myRegisterState extends State<myRegister> { ... }`: Mendefinisikan kelas `_myRegisterState` yang merupakan turunan dari `State` dan digunakan untuk mengatur state dari widget `myRegister`.</p>

5. `bool _isHidden = true;`: Membuat variabel `_isHidden` yang bertipe boolean dan diinisialisasi dengan `true`. Variabel ini digunakan untuk mengontrol visibilitas teks pada password field.</p>

6. `void _toggleVisibility() { ... }`: Metode `_toggleVisibility()` digunakan untuk mengubah nilai `_isHidden` menjadi negasi dari nilai saat ini. Metode ini akan dipanggil saat tombol toggle visibilitas password ditekan.</p>

7. `Widget build(BuildContext context) { ... }`: Override dari metode `build` yang digunakan untuk membangun dan mengatur tampilan widget `myRegister`.</p>

8. `SafeArea`: Widget `SafeArea` digunakan untuk memberikan area yang aman pada tampilan, sehingga menghindari tumpang tindih dengan elemen sistem seperti status bar atau bilah navigasi.</p>

9. `Container`: Widget `Container` digunakan untuk mengatur tampilan dan dekorasi dari area konten aplikasi.</p>

10. `Scaffold`: Widget `Scaffold` adalah kerangka utama aplikasi yang menyediakan fitur-fitur dasar seperti AppBar, Drawer, dan sebagainya.</p>

11. `AppBar`: Widget `AppBar` adalah komponen yang digunakan untuk menampilkan bilah aplikasi di bagian atas aplikasi. Di sini, AppBar tidak memiliki bayangan (`elevation: null`) dan memiliki warna latar belakang putih (`backgroundColor: Colors.white`).</p>

12. `IconButton`: Widget `IconButton` adalah tombol yang berisi sebuah ikon. Di sini, digunakan untuk tombol kembali dengan ikon panah ke belakang (`Icons.arrow_back_ios_rounded`).</p>

13. `Text`: Widget `Text` digunakan untuk menampilkan teks dengan gaya tertentu. Di sini, digunakan untuk menampilkan teks "REGISTER" dengan gaya yang ditentukan.</p>

14. `SingleChildScrollView`: Widget `SingleChildScrollView` digunakan untuk membuat area yang dapat digulir untuk konten yang panjang.</p>

15. `TextField`: Widget `TextField` digunakan untuk membuat input teks yang bisa diisi pengguna.</p>

16. `SizedBox`: Widget `SizedBox` digunakan untuk memberikan spasi kosong dengan ukuran tertentu.</p>

17. `ElevatedButton`: Widget `ElevatedButton` digunakan untuk membuat tombol dengan tampilan yang ditinggikan dan bayangan. </p>

# 6. Membuat Screen Forgot Password Flutter Dart </p></br>
Langkah selanjutnya adalah membuat Screen Forgot Password, caranya adalah sebagai berikut: </p>

<li> Buat File baru di Folder <b>lib</b> kita beri nama filenya yaitu <b>resetpass.dart</b>, Kemudian kita ketik codingan di dalam file tersebut. Berikut ini codingannya: </p></br>

```java

import 'package:flutter/material.dart';

class resetPassword extends StatefulWidget {
  const resetPassword({Key? key}) : super(key: key);

  @override
  _resetPasswordState createState() => _resetPasswordState();
}

class _resetPasswordState extends State<resetPassword> {
  @override
  Widget build(BuildContext context) {
    return SafeArea(
      child: Container(
        decoration: BoxDecoration(
          image: DecorationImage(
            image: AssetImage(
              'assets/login.jpg',
            ),
            fit: BoxFit.cover,
          ),
        ),
        child: Scaffold(
          backgroundColor: Colors.transparent,
          body: Stack(
            children: [
              Row(
                mainAxisAlignment: MainAxisAlignment.center,
                children: [
                  Container(
                    padding: EdgeInsets.only(
                      top: 65.0,
                    ),
                    child: Text(
                      'RESET \n PASSWORD',
                      textAlign: TextAlign.center,
                      style: TextStyle(
                        color: Colors.white,
                        fontSize: 40.0,
                      ),
                    ),
                  ),
                ],
              ),
              SingleChildScrollView(
                child: Container(
                  padding: EdgeInsets.only(
                    top: MediaQuery.of(context).size.height * 0.5,
                    left: 35,
                    right: 35,
                  ),
                  child: Column(
                    children: [
                      TextFormField(
                        obscureText: false,
                        decoration: InputDecoration(
                          labelText: 'Email',
                          prefixIcon: Icon(Icons.email_outlined),
                          fillColor: Color.fromARGB(255, 226, 234, 250),
                          filled: true,
                          // hintText: 'Password',
                          border: OutlineInputBorder(
                            borderRadius: BorderRadius.circular(10.0),
                          ),
                        ),
                      ),
                      SizedBox(height: 60.0),
                      Row(
                        mainAxisAlignment: MainAxisAlignment.end,
                        children: [
                          ElevatedButton(
                              style: ElevatedButton.styleFrom(
                                maximumSize: Size(170.0, 90.0),
                                minimumSize: Size(170.0, 60.0),
                                primary: const Color.fromARGB(255, 160, 14, 14),
                                shape: StadiumBorder(),
                              ),
                              onPressed: () {},
                              child: Row(
                                mainAxisAlignment:
                                    MainAxisAlignment.spaceBetween,
                                //crossAxisAlignment: CrossAxisAlignment.center,
                                children: [
                                  Text('RESET'),
                                  Icon(
                                    Icons.refresh,
                                    color: Color.fromARGB(255, 241, 241, 255),
                                  ),
                                ],
                              )),
                        ],
                      ),
                      SizedBox(height: 30.0),
                      Row(
                        mainAxisAlignment: MainAxisAlignment.spaceBetween,
                        children: [
                          TextButton(
                            onPressed: () {
                              Navigator.pushNamed(context, 'register');
                            },
                            child: Text(
                              'Register',
                              style: TextStyle(color: Color.fromARGB(255, 160, 14, 14)),
                            ),
                          ),
                          TextButton(
                            onPressed: () {
                              Navigator.pushNamed(context, 'login');
                            },
                            child: Text(
                              'LOGIN',
                              style: TextStyle(color: Color.fromARGB(255, 160, 14, 14)),
                            ),
                          ),
                        ],
                      ),
                    ],
                  ),
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }
}


```
</p></br>

Berikut ini adalah penjelasan dari codingan diatas: </p></br>

1. `class resetPassword extends StatefulWidget { ... }`: Mendefinisikan kelas `resetPassword` yang merupakan turunan dari `StatefulWidget`. `StatefulWidget` digunakan ketika widget memiliki state yang berubah selama masa hidupnya.</p>

2. `const resetPassword({Key? key}) : super(key: key);`: Konstruktor untuk kelas `resetPassword`. Ini menerima parameter `key` yang diperlukan oleh `StatefulWidget` superclass.</p>

3. `_resetPasswordState createState() => _resetPasswordState();`: Membuat instance dari `_resetPasswordState` yang merupakan subclass dari `State` untuk mengatur state dari widget `resetPassword`.</p>

4. `class _resetPasswordState extends State<resetPassword> { ... }`: Mendefinisikan kelas `_resetPasswordState` yang merupakan turunan dari `State` dan digunakan untuk mengatur state dari widget `resetPassword`.</p>

5. `Widget build(BuildContext context) { ... }`: Override dari metode `build` yang digunakan untuk membangun dan mengatur tampilan widget `resetPassword`.</p>

6. `SafeArea`: Widget `SafeArea` digunakan untuk memberikan area yang aman pada tampilan, sehingga menghindari tumpang tindih dengan elemen sistem seperti status bar atau bilah navigasi.</p>

7. `Container`: Widget `Container` digunakan untuk mengatur tampilan dan dekorasi dari area konten aplikasi.</p>

8. `Scaffold`: Widget `Scaffold` adalah kerangka utama aplikasi yang menyediakan fitur-fitur dasar seperti AppBar, Drawer, dan sebagainya.</p>

9. `DecorationImage`: Digunakan untuk menambahkan gambar latar belakang ke `Container` menggunakan `AssetImage` dengan fitur penyesuaian (`fit: BoxFit.cover`).</p>

10. `Row`: Widget `Row` digunakan untuk mengatur anak-anaknya secara horizontal.</p>

11. `Text`: Widget `Text` digunakan untuk menampilkan teks dengan gaya tertentu. Di sini, digunakan untuk menampilkan teks "RESET PASSWORD" dengan gaya yang ditentukan.</p>

12. `SingleChildScrollView`: Widget `SingleChildScrollView` digunakan untuk membuat area yang dapat digulir untuk konten yang panjang.</p>

13. `TextFormField`: Widget `TextFormField` digunakan untuk membuat input teks yang bisa diisi pengguna.</p>

14. `SizedBox`: Widget `SizedBox` digunakan untuk memberikan spasi kosong dengan ukuran tertentu.</p>

15. `ElevatedButton`: Widget `ElevatedButton` digunakan untuk membuat tombol dengan tampilan yang ditinggikan dan bayangan. Di sini, tombol "RESET" ditampilkan dengan ikon refresh (`Icons.refresh`).</p>

16. `Row`: Widget `Row` digunakan untuk mengatur anak-anaknya secara horizontal.</p>

17. `TextButton`: Widget `TextButton` digunakan untuk membuat tombol teks.</p>

18. `Navigator.pushNamed(context, 'register')`: Digunakan untuk mengarahkan navigasi ke halaman dengan rute bernama 'register'.</p>

