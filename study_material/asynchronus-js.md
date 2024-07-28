# Asynchronous Javascript Part 14
Selama ini code kalian berjalan synchronous (berurutan), kita akan belajar senjata powerful JS yaitu Asynchronous.

## Asynchronous JavaScript

JavaScript adalah bahasa pemrograman yang berjalan di lingkungan satu utas (single-threaded), yang berarti ia hanya dapat melakukan satu tugas pada suatu waktu. Namun, JavaScript memiliki dukungan untuk operasi asynchronous yang memungkinkan eksekusi tugas lain tanpa menghentikan jalannya program utama. Operasi asynchronous sangat penting dalam pengembangan web modern, terutama ketika berhadapan dengan operasi jaringan, I/O, dan tugas yang membutuhkan waktu lama.

1. **Synchronous vs. Asynchronous**

**Synchronous (Blocking)**:
Dalam operasi synchronous, setiap tugas dieksekusi satu per satu secara berurutan. Ketika suatu tugas sedang berjalan, program akan terhenti dan tidak dapat melanjutkan ke tugas berikutnya hingga tugas saat ini selesai.
```js
Contoh:
console.log('1');
console.log('2');
console.log('3');
```
Output: 1, 2, 3 (dieksekusi berurutan)

**Asynchronous (Non-Blocking)**:
Dalam operasi asynchronous, tugas-tugas yang membutuhkan waktu lama atau bergantung pada eksternal seperti jaringan atau berkas, dieksekusi secara terpisah. Program utama tetap berjalan tanpa harus menunggu tugas tersebut selesai.

Contoh:
```js
console.log('1');
setTimeout(() => {
  console.log('2');
}, 1000);
console.log('3');
```
Output: 1, 3, 2 (2 ditunda selama 1 detik)

<br/>

2. **Callbacks**:


Callback adalah sebuah fungsi yang dilewatkan sebagai argumen ke dalam fungsi lain dan dijalankan setelah fungsi tersebut selesai. Ini adalah salah satu cara umum untuk mengelola operasi asynchronous.

Contoh:
```js
function fetchData(callback) {
  setTimeout(() => {
    const data = 'Some data';
    callback(data);
  }, 1000);
}

fetchData((result) => {
  console.log(result);
});
```

3. **Promises**:

Promises adalah pola yang lebih modern untuk mengelola operasi asynchronous. Sebuah Promise merepresentasikan nilai yang mungkin tersedia sekarang, nanti, atau tidak sama sekali. Promise memiliki tiga status: pending, fulfilled, atau rejected.

Contoh:
```js
function fetchData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const data = 'Some data';
      resolve(data);
    }, 1000);
  });
}

fetchData()
  .then((result) => {
    console.log(result);
  })
  .catch((error) => {
    console.error(error);
  });
```

4. **Async/Await**:

Async/Await adalah pendekatan modern yang memungkinkan penulisan kode asynchronous dengan gaya yang mirip dengan kode synchronous. Ini berdasarkan Promise.

Contoh:
```JS
function fetchData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const data = 'Some data';
      resolve(data);
    }, 1000);
  });
}

async function main() {
  try {
    const result = await fetchData();
    console.log(result);
  } catch (error) {
    console.error(error);
  }
}

main();
```



5. **Set Timeout Function**:
setTimeout adalah sebuah fungsi dalam JavaScript yang digunakan untuk menunda eksekusi suatu fungsi atau blok kode selama waktu tertentu. Fungsi ini sering digunakan untuk mensimulasikan operasi yang memakan waktu seperti mengambil data dari server, melakukan tugas berat, atau menjalankan suatu tugas setelah beberapa saat.

Pada dasarnya, setTimeout menerima dua argumen:
Fungsi atau kode yang akan dieksekusi setelah waktu tertentu.
Waktu (dalam milidetik) sebagai waktu penundaan sebelum eksekusi.

Contoh penggunaan setTimeout:
```JS
setTimeout(() => {
  console.log('This code will be executed after 1000 milliseconds (1 second).');
}, 1000);
```


Dalam konteks tugas yang diberikan, setTimeout digunakan untuk mensimulasikan pengambilan data dari server atau operasi lain yang memerlukan waktu. Ini memungkinkan kita untuk menggambarkan penggunaan pendekatan asynchronous dalam JavaScript, di mana kita dapat melanjutkan eksekusi kode lain sementara menunggu operasi selesai. 

Operasi asynchronous sangat penting dalam lingkungan JavaScript, terutama dalam pengembangan aplikasi web yang cenderung berkomunikasi dengan server, melakukan I/O, dan menjalankan tugas yang memakan waktu. Penggunaan pendekatan asynchronous memastikan bahwa aplikasi tetap responsif dan tidak terjebak dalam blok yang menghambat jalannya program.