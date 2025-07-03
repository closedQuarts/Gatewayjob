📘 JobFinder API Gateway
Bu proje, JobFinder sisteminde API Gateway görevi görür. Tüm mikro servis çağrıları tek bir giriş noktasından yönlendirilir.

🔗 Gateway URL
https://jobfindergateway-eshpcwedgjc6f6hs.northeurope-01.azurewebsites.net

🎯 Amaç
Tüm backend servislerini tek endpoint üzerinden erişilebilir kılmak.

Servislerin versiyonlamasını yönetmek.

Gerektiğinde load balancing ve rate limit uygulayabilmek.

🛠️ Kullanılan Teknolojiler
.NET 8 Web API

Ocelot API Gateway

Azure App Services (deployment)

🔧 Yapılandırma (ocelot.json)
Örnek Ocelot yapılandırması:

json
Kopyala
Düzenle
{
  "Routes": [
    {
      "DownstreamPathTemplate": "/api/v1/{everything}",
      "DownstreamScheme": "https",
      "DownstreamHostAndPorts": [
        {
          "Host": "jobfinderapi4458-d3g6fkgca2cfaahb.northeurope-01.azurewebsites.net",
          "Port": 443
        }
      ],
      "UpstreamPathTemplate": "/api/v1/{everything}",
      "UpstreamHttpMethod": [ "GET", "POST", "PUT", "DELETE" ]
    }
  ],
  "GlobalConfiguration": {
    "BaseUrl": "https://jobfindergateway-eshpcwedgjc6f6hs.northeurope-01.azurewebsites.net"
  }
}
🚀 Yayınlama
Azure Portal üzerinden App Service olarak deploy edilmiştir.
