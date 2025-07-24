# 🎬 Film Keşif Platformu API

Modern ve ölçeklenebilir film keşif platformu için geliştirilmiş kapsamlı RESTful API. Clean Architecture prensiplerine uygun olarak tasarlanmış, CQRS ve Mediator pattern'larını kullanan güçlü bir backend sistemi.

## 📋 Proje Hakkında

Bu proje, film severler için tasarlanmış modern bir keşif platformunun backend API'sidir. Kullanıcılar filmler hakkında detaylı bilgi alabilir, kategorilere göre arama yapabilir, oyuncu bilgilerini görüntüleyebilir ve kendi film listeleri oluşturabilir.

### ✨ Temel Özellikler

- 🎯 **Film Yönetimi**: Kapsamlı film bilgileri ve meta verileri
- 🎭 **Oyuncu Kataloğu**: Detaylı oyuncu profilleri ve filmoğrafisi
- 🏷️ **Kategori Sistemi**: Esnek film kategorileme ve filtreleme
- ⭐ **Değerlendirme Sistemi**: Kullanıcı yorumları ve puanlama
- 🔍 **Gelişmiş Arama**: Çoklu kriterlerde arama ve filtreleme
- 👤 **Kullanıcı Yönetimi**: Güvenli kayıt ve giriş sistemi
- 📱 **RESTful API**: Modern web standartlarında API tasarımı

## 🏗️ Sistem Mimarisi

Proje **Clean Architecture** prensiplerine uygun olarak 4 ana katmanda organize edilmiştir:

```
MovieApi/
├── 📁 Core/                    # İş mantığı katmanı
│   ├── MovieApi.Application/   # Uygulama servisleri
│   └── MovieApi.Domain/        # Domain modelleri
├── 📁 Infrastructure/          # Altyapı katmanı
│   └── MovieApi.Persistence/   # Veritabanı erişimi
├── 📁 Presentation/           # Sunum katmanı
│   └── MovieApi.WebApi/       # RESTful API
└── 📁 Frontends/              # Kullanıcı arayüzü
    ├── MovieApi.WebUI/        # MVC Web arayüzü
    └── MovieApi.Dto/          # Veri transfer objeleri
```

### 🎨 Kullanılan Design Pattern'lar

- **CQRS (Command Query Responsibility Segregation)**: Okuma ve yazma işlemlerinin ayrıştırılması
- **Mediator Pattern**: Loosely coupled iletişim
- **Repository Pattern**: Veri erişim katmanının soyutlanması
- **Dependency Injection**: Bağımlılık yönetimi

## 🚀 Teknoloji Stack'i

### Backend

- **🔧 .NET 9.0**: Modern framework
- **🏗️ ASP.NET Core Web API**: RESTful servisler
- **🗄️ Entity Framework Core**: ORM
- **🔍 LINQ**: Veri sorgulama
- **📊 SQL Server**: Veritabanı
- **🔐 ASP.NET Core Identity**: Kimlik doğrulama

### Tasarım Desenleri ve Kütüphaneler

- **📡 MediatR**: Mediator pattern implementasyonu
- **🔄 AutoMapper**: Nesne haritalama
- **📝 Swagger/OpenAPI**: API dokümantasyonu
- **✅ FluentValidation**: Validation kuralları

### Frontend

- **🌐 ASP.NET Core MVC**: Web arayüzü
- **🎨 Bootstrap**: UI framework
- **⚡ JavaScript**: Dinamik etkileşimler

## 📚 API Endpoint'leri

### 🎬 Film İşlemleri

```http
GET    /api/Movies              # Tüm filmleri listele
GET    /api/Movies/{id}         # Belirli film detayları
POST   /api/Movies              # Yeni film ekle
PUT    /api/Movies              # Film güncelle
DELETE /api/Movies/{id}         # Film sil
```

### 🏷️ Kategori İşlemleri

```http
GET    /api/Categories          # Kategorileri listele
GET    /api/Categories/{id}     # Kategori detayları
POST   /api/Categories          # Kategori ekle
PUT    /api/Categories          # Kategori güncelle
DELETE /api/Categories/{id}     # Kategori sil
```

### 🎭 Oyuncu İşlemleri

```http
GET    /api/Casts               # Oyuncuları listele
GET    /api/Casts/{id}          # Oyuncu detayları
POST   /api/Casts               # Oyuncu ekle
PUT    /api/Casts               # Oyuncu güncelle
DELETE /api/Casts/{id}          # Oyuncu sil
```

### 🏷️ Etiket İşlemleri

```http
GET    /api/Tags                # Etiketleri listele
GET    /api/Tags/{id}           # Etiket detayları
POST   /api/Tags                # Etiket ekle
PUT    /api/Tags                # Etiket güncelle
DELETE /api/Tags/{id}           # Etiket sil
```

### 👤 Kullanıcı İşlemleri

```http
POST   /api/Registers           # Kullanıcı kaydı
```

## ⚙️ Kurulum ve Çalıştırma

### Gereksinimler

- .NET 9.0 SDK
- SQL Server (LocalDB veya tam sürüm)
- Visual Studio 2022 veya Visual Studio Code

### Adım Adım Kurulum

1. **Projeyi klonlayın**

```bash
git clone [repo-url]
cd MovieApi
```

2. **Bağımlılıkları yükleyin**

```bash
dotnet restore
```

3. **Veritabanı bağlantısını yapılandırın**
   `Infrastructure/MovieApi.Persistence/Context/MovieContext.cs` dosyasında connection string'i güncelleyin:

```csharp
optionsBuilder.UseSqlServer("Server=(localdb)\\mssqllocaldb;Database=MovieApiDb;Trusted_Connection=true;");
```

4. **Veritabanı migration'larını çalıştırın**

```bash
cd Infrastructure/MovieApi.Persistence
dotnet ef database update
```

5. **API'yi çalıştırın**

```bash
cd Presentation/MovieApi.WebApi
dotnet run
```

6. **Web UI'yi çalıştırın (isteğe bağlı)**

```bash
cd Frontends/MovieApi.WebUI
dotnet run
```

### 🌐 Erişim URL'leri

- **API**: `https://localhost:7001`
- **Swagger UI**: `https://localhost:7001/swagger`
- **Web UI**: `https://localhost:7002`

## 📖 API Dokümantasyonu

Proje çalıştığında Swagger UI üzerinden detaylı API dokümantasyonuna erişebilirsiniz: `https://localhost:7001/swagger`

## 🗄️ Veritabanı Şeması

### Ana Tablolar

- **Movies**: Film bilgileri
- **Categories**: Film kategorileri
- **Casts**: Oyuncu bilgileri
- **Tags**: Film etiketleri
- **Reviews**: Kullanıcı yorumları
- **AspNetUsers**: Kullanıcı bilgileri (Identity)

## 🔧 Konfigürasyon

### Ortam Değişkenleri

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Your-Database-Connection-String"
  },
  "JwtSettings": {
    "SecretKey": "Your-JWT-Secret-Key",
    "Issuer": "MovieApi",
    "Audience": "MovieApi-Users"
  }
}
```

## 🤝 Katkıda Bulunma

1. Fork yapın
2. Feature branch oluşturun (`git checkout -b feature/YeniOzellik`)
3. Commit yapın (`git commit -am 'Yeni özellik eklendi'`)
4. Push yapın (`git push origin feature/YeniOzellik`)
5. Pull Request oluşturun
