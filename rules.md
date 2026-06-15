# Google Antigravity - Core Rules for Native PHP / cPanel Stack

## 1. Zero-Framework Policy (Backend)
- KESİNLİKLE Laravel, Symfony, CodeIgniter, Slim veya benzeri hiçbir PHP framework'ü KULLANMA ve ÖNERME.
- Proje tamamen %100 Native (Vanilla) PHP 8+ ile geliştirilecektir.
- ORM (Eloquent, Doctrine vb.) KULLANILMAYACAKTIR. Veritabanı işlemleri sadece saf PDO (PHP Data Objects) ve raw SQL sorguları ile yapılacaktır.
- Şablon motoru (Twig, Blade vb.) KULLANILMAYACAKTIR. Görünümler (Views) için saf PHP ve HTML entegrasyonu kullanılacaktır.

## 2. Veritabanı (MySQL)
- SADECE MySQL veya MariaDB kullanılacaktır. (PostgreSQL, SQLite, MongoDB önerme).
- Eski `mysql_*` veya `mysqli_*` yerine DAİMA `PDO` kullanılacaktır.
- Tüm dış veriler PDO Prepared Statements (Hazırlanmış İfadeler) ile bağlanacak, asla SQL string'ine doğrudan değişken eklenmeyecektir.

## 3. Deployment ve Sunucu
- Git, GitHub, GitLab, Docker, Kubernetes, CI/CD pipeline'ları KESİNLİKLE YOKTUR ve ÖNERİLMEYECEKTİR.
- Bütün deployment süreçleri doğrudan cPanel (File Manager, FTP/SFTP) mantığına uygun olacaktır. Hedef dizin `public_html`'dir.
- Sunucu komut satırı (SSH) erişimi, `composer` veya `npm` bağımlılıkları gerektiren sunucu tarafı komutları KULLANILMAYACAKTIR.

## 4. Native Mimari Standartları
- Yönlendirme (Routing) işlemleri için `.htaccess` üzerinden tüm istekleri `index.php`'ye yönlendir ve rotaları saf PHP ile ayrıştır.
- Oturum yönetimi için sadece native `session_start()` ve `$_SESSION` yapılarını kullan.
