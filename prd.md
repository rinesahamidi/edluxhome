# SHABLLON PRD (Product Requirements Document) — 1 Faqe

**Shkurtesat:** PWA (Progressive Web App – aplikacion web progresiv); PRD (Product Requirements Document – dokumenti i kërkesave të produktit); MVP (Minimum Viable Product – produkti minimal i përdorshëm).
**Kursi:** Programimi për Pajisje Mobile (2026/2027) • **Kolegji AAB**  
**Emri i Projektit:** edluxhome  
**Themeluesi / Ekipi:** Rinesa Hamidi RE-02242/24
**Data & Versioni:** Java 02 • Versioni 1.0 (Draft për MVP)

---

## 1. Përdoruesi dhe Problemi Real
- **Kush e përjeton dhimbjen?** Personat qe duan te dekorojne shtepine/banjon (pasqyra, vazo lulesh, aksesore banje) dhe nuk gjejne gjithcka ne nje vend te organizuar online.
- **Kur ndodh?** Kur dikush zhvendoset ne shtepi te re, rinovon banjon, ose kerkon dhurate dekorative dhe s'ka kohe te vizitoje disa dyqane fizike.
- **Si e zgjidhin sot?** Vizitojne 2-3 dyqane fizike per te krahasuar cmime/stile, ose blejne rastesisht nga shpallje te shperndara ne Facebook/Instagram, pa katalog apo cmime te qarta.

## 2. Evidenca e Vëzhgimit (3 Bisedat me Përdoruesit)
- **Biseda 1 (Klientja - blerese dekori): "Dua nje pasqyre te bukur, po duhet me shku ne 3 dyqane per me pa cka kane dhe sa kushtojne.""*
- **Biseda 2 (Klienti - rinovim banje): "Kerkova set banje (shishe sapuni, mbajtese furce dhembesh) qe te pershtaten ne ngjyre, e humba dite te tere duke krahasuar neper dyqane."*
- **Biseda 3 (Klientja - dhurate): "Do te doja me porosit nje vazo online dhe me e marr ne shtepi, pa u dashur me shku fizikisht dhe pa u dashur me shkru mesazhe per me pyt cmimin."*

## 3. Hipoteza e Vlerës
> **Nëse** u ofrojme klienteve nje aplikacion mobil (PWA) ku shfletojne katalogun e produkteve dekorative (pasqyra, vazo, aksesore banje) me foto dhe cmime te qarta, shtojne ne shporte dhe bejne porosine direkt ne app,  
> **atëherë** klientet do te kursejne kohen e vizitave ne dyqane fizike, do te kene qasje ne katalog kudo qofshin, dhe pronari do te marre porosi te organizuara ne vend te mesazheve te shperndara.

## 4. Rrjedha Kryesore e Përdoruesit (Core Flow — Max 5 Hapa)
Hyrja: Klienti hap app-in dhe shikon katalogun (kategori: Pasqyra, Vazo, Banjo).
Shfletimi: Klienti zgjedh nje kategori dhe shikon produktet me foto dhe cmim.
Shtimi ne shporte: Klienti shtyp [Shto ne Shporte] per produktin e zgjedhur.
Porosia: Klienti plotson te dhenat e dorezimit (emer, adrese, telefon) dhe konfirmon porosine.
Konfirmimi: Sistemi ruan porosine dhe klienti sheh mesazhin "Porosia u prit".

## 5. Kufijtë e MVP-së (Scope Contract)
- **BRENDA MVP-së (Maksimumi 3 funksione):**
  1. Katalog produktesh me kategori, foto dhe cmim (Supabase si baze te dhenash).
  2. Shporte blerjesh (cart) brenda app-it, per me shume produkte njekohesisht.
  3. Krijimi i porosise (checkout) qe ruhet ne baze te dhenash, me pagese "cash ne dorezim".
- **JASHTË MVP-së (Të përjashtuara qëllimisht për këtë semestër):**
  - Zero pagese online me kartele bankare (Visa/Mastercard/PayPal); pagesa mbetet cash ne dorezim.
  - Zero panel i avancuar admin per menaxhim stoku (produktet shtohen manualisht ne Supabase per tani).
  - Zero sistem rekomandimesh/kerkimi te avancuar (filtrim vetem sipas kategorise, jo AI apo kerkim tekstual).

## 6. Kriteret e Pranimit (Acceptance Criteria - Çfarë testohet)
- [ ] **AC-1:** Kur klienti hap kategorine "Pasqyra", shfaqen vetem produktet e asaj kategorie me foto dhe cmim.
- [ ] **AC-2:** KKur klienti shton nje produkt ne shporte, numri i artikujve ne ikonen e shportes rritet me 1.
- [ ] **AC-3:** Kur klienti konfirmon porosine, ajo ruhet ne Supabase me statusin "Ne pritje" dhe shporta zbrazet.
- [ ] **AC-4:** Aplikacioni hapet dhe mund te shfletohet edhe kur lidhja e internetit eshte e dobet (PWA baze).

## 7. Modeli Minimal i të Dhënave (Supabase PostgreSQL)
```sql
products (id, name, category, price_eur, image_url, description, stock)
orders (id, customer_name, phone, address, status, created_at)
order_items (id, order_id, product_id, quantity, price_eur)
```

## 8. Rreziku Kryesor që Duhet Testuar
- **Rreziku:**A do te besojne klientet te bejne porosi online (me pagese cash ne dorezim) pa pare produktin fizikisht apo pa e njohur markes?
- **Testi në Javën 2:** Foto te qarta e cilesore te produkteve plus cmim i sakte mjaftojne per te krijuar besimin fillestar te blerjes.
