### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a>Usuwanie Ssl3 WCF TransportDefaults

|   |   |
|---|---|
|Szczegóły|Używając NetTcp za pomocą zabezpieczeń transportu i poświadczeń typu certyfikatu protokołu SSL 3 nie jest już domyślny protokół używany do negocjowania bezpiecznego połączenia. W większości przypadków należy bez wpływu na istniejące aplikacje jako protokół TLS 1.0 zawsze została uwzględniona na liście protokół dla NetTcp. Wszyscy istniejący klienci powinno być możliwe negocjowania połączenia przy użyciu w co najmniej TLS1.0.|
|Sugestia|Jeśli wymagana jest Ssl3, umożliwia jedną z następujących mechanizmów konfiguracji Dodawanie Ssl3 do listy wynegocjowanym protokołów.<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[<](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li>[&lt;sslStreamSecurity&gt; części &lt;customBinding&gt;] ~ / docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</li></ul>|
|Zakres|Krawędź|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType></li></ul>|

