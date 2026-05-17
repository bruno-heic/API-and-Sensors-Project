# Google ATM — Exploração Urbana 3D & Pressão Atmosférica
![React Native](https://img.shields.io/badge/React_Native-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![Expo](https://img.shields.io/badge/Expo-000020?style=for-the-badge&logo=expo&logoColor=white)
![MapLibre](https://img.shields.io/badge/MapLibre-4E9A06?style=for-the-badge&logo=maplibre&logoColor=white)

O **Google ATM** é um aplicativo mobile desenvolvido em React Native e Expo que combina geoprocessamento avançado, renderização de mapas em três dimensões e leitura de sensores barométricos nativos. O projeto foi desenhado sob uma identidade visual limpa e minimalista inspirada nas diretrizes do *Material Design* e UI do Google.

---

## Funcionalidades do Aplicativo

### Monitoramento Atmosférico Real (`AboutScreen`)
* **Sensor de Pressão Local:** Conecta-se diretamente ao hardware do dispositivo utilizando o `expo-sensors` para monitorar a pressão atmosférica em hectopascais (hPa).
* **Altímetro Relativo:** Caso o dispositivo possua o sensor físico, o aplicativo calcula a altitude aproximada utilizando a fórmula hidrostática padronizada:
  
      const calculateApproxAltitude = (p) => {
        if (!p) return 0;
        return Math.round(44330 * (1 - Math.pow(p / 1013.25, 1 / 5.255))))
      };
  
* **Fallback Inteligente:** Em aparelhos sem barômetro físico, o app detecta a ausência de forma segura e exibe dados simulados estáveis de referência (1013.2 hPa) para manter a usabilidade da interface.

###  Projeção Urbana 3D e Geolocalização (`HomeScreen`)
* **Mapas Volumétricos:** Utiliza `react-native-webview` para renderizar malhas de edifícios em 3D em tempo real via **MapLibre GL** e a API open-source **OpenFreeMap**.
* **Controle de Câmera Dinâmico:** Navegação fluida com transições suaves de aproximação (*flyTo*), ângulo de inclinação (*pitch* a 45°) e rotação.
* **Busca com Autocomplete:** Integração com o motor de busca **Nominatim (OpenStreetMap)** para encontrar localidades ao redor do globo com atraso inteligente (*debounce*) de digitação para otimizar requisições.
* **Minha Localização:** Acesso ao GPS nativo via `expo-location` para reposicionar o mapa instantaneamente onde o usuário está.

### Análise Bioclimática Inteligente
* **Integração com Open-Meteo:** Cruza coordenadas geográficas com dados climáticos globais em tempo real (temperatura, umidade relativa e códigos de clima WMO).
* **Painel de Insights:** Algoritmo dedicado que avalia o ambiente e emite badges de status e recomendações de bem-estar para atividades externas (Ex: *Excelente*, *Moderado*, *Desconfortável*, *Ruim*).

---

## Tecnologias Utilizadas

* **Framework Base:** React Native & Expo (SDK Workflow)
* **Sensores de Hardware:** `expo-sensors` (Barometer) & `expo-location` (GPS)
* **Componentes Web:** `react-native-webview`
* **Renderização de Mapas:** MapLibre GL & OpenFreeMap (Estilo *Bright* com extrusão 3D)
* **APIs Web:** OpenStreetMap Nominatim (Geocoding) & Open-Meteo API (Weather Forecast)
* **Ícones:** `@expo/vector-icons` (FontAwesome5 & MaterialCommunityIcons)

---

## Integrantes da Dupla
* Nome: **Bruno Souza Guerra**
* Nome: **Giovanna Cintra Santana**