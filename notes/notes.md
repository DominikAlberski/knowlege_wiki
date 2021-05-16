ewa.stańczyk@admad.io
bartek.luchowski@admad.io ???

Atrybucja
reklama nowa strona reklama
przeklikanie przez pewne strony

domeny
W db seeds ustawią się domeny i rynek na których działają nie powinno
model - Facebook::Pixel

model zawiera więcej domen niż seed file

extra sales menago - serwis do email marketingu / webhookami, integracja z sales menago jest rozsypana przestaja wspierac api, teraz działa tylko na polsce

Jedna domena powinna być na 1 rynek

Seedy muszą być indepotentne

Trzeba dodać pliki statycznie i dodać seedy

Ogólnie 2 rodziaje stron
artykół - bez formularzy
 link musi zawierać w href="promotianal-page" - zaszłość implementacyjna
centrum - z formularzem

Znaleźć stronę w public


Nowe wdrożenie

Wdrożenie centrum
config sprawdzenie slug
sprawdzenie w aplikcaji czy jest w public strona
pobieranie kontetnu do katalogu public


Opis raportu XLS

chodzi o to aby wyniki

Wdrożenie na isteniejący LP
Wywalenie wszystkiego z istniejącego katalogu
odpalenie skryptu
wklejeniu linku do taska "using link:"

w przypadku nowej strony dodać ją do seedów w weebsite
dodać produkty do głównych seedów

---

order id: 1069621


--- 

automatycznie wysyłanie kompensaty odliczanie na poczet fv

wszystko co jest w kopmensatch jest w raportach cod

nie wiemy czy kompensaty pokrywają się zpłątnościami
Czy mamy wszystkie raporty DPD? mamy 92 czy to wszystkie raporty.
Zsumować fv od dpd i zobaczyć ile przesłaliśmy do dpd kwota kompensat + kwota przelewów = kwacie fv od dpd.

Ile mieliśmy wypracowanego CoD jeżeli nie zgadza się z raportami to skąd wynika różnica

Potwierdzić kwotę 11m u nich ile powinni przysłać nam raportów

---

Dodać stopkę w mailu

Po okresie próbnym

House Rules Slack

Where are you know - informacje o urlopie plus info w kalendarzu
Profil na slacku - uzupełnić

Workflow
scrum - agile
	- standupy
	- pivot, trello, notion
Czas w clockify
wybranie projekt i logowanie rzeczy związane z projektem
o 13 daily projektowe
2 blogi dev news , zdalni.pl

feedback - jest po 1 albo po 3 miesiącu, i na tej podstawie dalsza rozmowa,
później co ~6m
2 FE, BE ja + ? + Miko

order_meta
dpd_label
markets
line_items
gift
products
categories
traits
vat_invoice_vendors
vat_invoice_registers
vat_invoice_register_entry_vat_groups

```ruby
  def model_to_fixture(model:, scope:, ids:)
    constantize(model)
      .where(scope, ids)
  end

  def model_fixture_creator(model:, attributes_anonymezed: {})
    table_name = model.table_name
    path = Rails.root.join(
      format("/spec/fixtures/%<table>s.yml", table: table_name)
    )

    File.open(path, "w") do |f|
      data_for_file = {}
      counter = 0
      model_to_fixture(model: model, scope: scopes[table_name], ids: )
        .in_batches(of: 100) do |batch|
          data = batch.inject({}) do |memo_hash, table|
            counter += 1
            memo_hash["#{table.id}_#{counter}"] = table.attributes.dup.merge(attributes_anonymezed)
            memo_hash
          end
          data_for_file = data_for_file.merge(data)
        end
      f.write(data_for_file.to_yaml)
    end
  end

  def scopes
    scopes = Hash.new('order_id in (?)')
    scopes.merge({
      "user_languages" => 'id in (?)', #markets_for_fixtures.pluck(:user_language_id)
      "markets" => "participant_id in (?) AND participant_type = 'Order'",
    })
  end

  def ids
    ids = Hash.new(orders_for_fixtures.pluck(:id))
    ids.merge({
      "user_languages" => model_to_fixture(model: Market, scope: scopes["markets"], ids: orders_for_fixtures.pluck(:id)),
    })
  end
```

---

font 10px

Ubile Sp. z o. o., NIP: 701-03-59-284 ul. Idzikowskiego 14, 00-710 Warszawa

Allepharm Limited S.K.A., NIP: 525-268-70-16 ul. Jana III Sobieskiego 110, 00-764 Warszawa