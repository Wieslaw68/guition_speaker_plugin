# Guition Speaker — plugin Tessera

Plugin sprzętowy dla **Guition ESP32-S3-4848S040**. Dodaje do ekranu wyjście głośnikowe I2S oraz encję `media_player` Home Assistant. Obsługuje odtwarzanie mediów i komunikaty TTS z Home Assistant.

## Co zawiera

- Głośnik NS4168 jako zewnętrzny DAC I2S.
- Odtwarzacz Home Assistant (`speaker_source`).
- Oddzielne tory dla komunikatów i muzyki; komunikaty mają priorytet.
- Audio wyłącznie **MONO**, 48 kHz / 16 bit.
- Regulację głośności w ustawieniach ekranu.
- Bez mikrofonu i bez funkcji nasłuchu.

## Połączenia

| Sygnał | GPIO |
|---|---:|
| I2S BCLK | GPIO1 |
| I2S LRCLK | GPIO2 |
| I2S DATA OUT | GPIO40 |

Konfiguracja odpowiada wariantowi płytki z głośnikiem NS4168. Zwory muszą być ustawione dla głośnika, a nie dla przekaźników. Nie używaj jednocześnie przekaźników na tych samych liniach.

## Instalacja

1. W Tessera otwórz **Plugins**.
2. Wybierz **Add with a link** i wskaż repozytorium zawierające ten katalog pluginu (po umieszczeniu go w GitHub).
3. Wybierz ekran **Guition ESP32-S3-4848S040** i zainstaluj plugin.
4. Po kompilacji sprawdź w Home Assistant integrację ESPHome — urządzenie powinno udostępnić encję odtwarzacza mediów.
5. W automatyzacjach i usługach TTS używaj encji odtwarzacza przypisanej do tego ekranu.
6. W Tessera w ustawieniach włącz media (wygaszacz ekranu u mnie działa jako Panel Media Player).

## Test / ograniczenia

Manifest deklaruje API Tessera `0.24`, wymaga PSRAM i pasuje wyłącznie do board key `guition`. Składnia YAML i manifest są walidowane lokalnie. Nie wykonano pełnej kompilacji ESPHome ani testu na fizycznej płytce; przed codziennym użyciem należy wykonać build i sprawdzić odtwarzanie/TTS na urządzeniu.

## Przed publikacją

W `tessera-plugin.yaml` pole `maintainer: local` jest wartością tymczasową. Przed publikacją w katalogu Tessera zastąp je właściwą nazwą konta GitHub. Wersja `0.1.0` jest wersją początkową.
