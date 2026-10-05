# SOLID - Interface Segregation Principle (ISP) Lab Çözümü

Bu repository, Yazılım Mimari Tasarımı dersi kapsamındaki hesap makinesi ödevinin çözümünü içermektedir.

## Problem (Mevcut Durum)
Başlangıç kodunda her şeyi yapabilen, tek ve devasa bir "Fat Interface" (`Calculator`) tasarımı bulunmaktaydı[cite: 6]. Bu durum, sadece temel işlemleri kullanacak olan `BasicCalculator` gibi sınıfların hiç kullanmadığı bilimsel ve bitsel metotları da (`UnsupportedOperationException` fırlatarak veya boş bırakarak) içermesine yol açıyordu[cite: 2, 4, 7]. Bu yapı, **Arayüz Ayrıştırma Prensibini (ISP)** ihlal etmekteydi[cite: 3].

## Çözüm ve Tasarım Gerekçesi
Mevcut krizleri (Derleme Tuzağı / Compilation Trap) önlemek adına monolitik arayüz rollerine göre parçalandı[cite: 3, 9]:
- `BasicCalculatorInterface`: Temel 4 işlemi barındırır.
- `ScientificCalculatorInterface`: Bilimsel işlemleri barındırır.
- `ProgrammingCalculatorInterface`: Bitsel işlemleri barındırır.

Sınıflar yalnızca ihtiyaç duydukları arayüzleri implement edecek şekilde refactor edildi. `CalculatorMain` üzerindeki mevcut davranışlar ve çıktılar tamamen korundu.