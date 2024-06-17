# `RusLawOD`: Открытые данные о российском законодательстве
«RusLawOD» — это корпус текстов законодательных актов Российской Федерации и их метаданных за период с 1991 по 2023 год. В корпусе собраны все 281 413 текстов (176 523 268 токенов) законов, несекретных федеральных постановлений и актов вместе с их метаданными.

`Версия 2`

## Научное цитирование

Если вы используете корпус в ваших научных работах, ссылаться можно на препринт: The Russian Legislative Corpus. Russian Law Open Data. arXiv preprint arXiv:2406.04855 (2024).

## Состояние дел
Российское законодательство публикуется в официальных бумажных журналах с 1990 года. С 1990 года нормативные правовые акты не могут вступить в силу без официального опубликования. Некоторые попытки создания электронных баз данных правовых актов были предприняты в 1980-х годах. В начале 1990-х годов коммерческие информационные компании создали собственные базы данных по законодательству и судебным решениям. С 2011 года нормативные акты предполагается официально публиковать на Официальном интернет-портале правовой информации ([pravo.gov.ru](http://pravo.gov.ru)). Сейчас оно включает в себя как федеральное, региональное, так и муниципальное законодательство, однако информация не является полной. Но такие документы существуют только в графическом формате (сканированные TIFF или PDF без текстового слоя). Мы используем наиболее удобный источник, который можно считать наиболее авторитетным: «ИПС Законодательство РФ» (Информационно-правовая система «Законодательство Российской Федерации», входящая в состав портала pravo.gov.ru, но не являющаяся считается официальной публикацией (т.е. дата публикации в этом источнике не может считаться датой официальной публикации и текст не имеет такого же правового статуса, как текст с подписью).

## О представленном корпусе
Представленный корпус (в версии `0.5`) состоит из 458,884 файлов в формате XML содержащие тексты федеральных законов, указов Президента РФ, постановлений правительства и других органов власти Россиской Федерации, ее субъектов, некоторых муниципальных органов, принятых по состоянию на конец 2017 г. файлы XML также содержат метаданные о документах.

Этот корпус (версия 2) состоит из XML-файлов, содержащие тексты законов Российской Федерации, указов Президента РФ, постановлений  Правительства, и другие виды актов, опубликованные по состоянию на 31 декабря 2023 г. XML-файлы содержат метаданные, извлеченные из источника, и соответствующие тексты.

## Схема
Важно, чтобы данные репозитория были представлены в удобном и совместимом формате. Мы ориентируемся на стандарт [Akoma Ntoso](http://www.akomantoso.org/). Оговоримся, что сейчас корпус не вполне соответствует ему, поскольку мы еще не размечаем внутреннюю структуру текста.

## Структура XML
Структура XML показана на нижеследующем примере с комментариями. Все поля не являются обязательными и присутствуют только если информация есть в источнике.

```xml
<act> <!-- Legal act as the type of a document -->
  <meta> <!-- major sections are metadata and text -->
    <identification> <!-- see the Limitations on information about legal act identification in Russia -->
      <pravogovruNd val="000000000" /> <!-- document internal number at the IPS Zakonodatelstvo 
      website at the moment of download. It may be subject to change -->
      <issuedByIPS val="Entity that issued the act according to the IPS Zakonodatelstvo" />
      <docdateIPS val="00.00.0000" /> <!-- document day of signature according to the IPS 
      Zakonodatelstvo, date format is dd.mm.yyyy-->
      <docNumberIPS val="000" /> <!-- document number at signature according to the IPS Zakonodatelstvo -->
      <headingIPS>title of the document in the IPS Zakonodatelstvo.</headingIPS> 
      <doc_typeIPS val="Document type as was in the source"/>
      <doc_author_normal_formIPS val="State organ that adopted the act, in normal language form"/>
      <signedIPS val="______"/> <!-- Person name who signed this legal act as provided in the source -->
      <statusIPS val="Утратил силу"/> <!-- In force, Not in force, In force with amendments: Acting status at the date of scrapping and as it was provided by the source -->
      <actual_datetimeIPS val="1710792705.7460072"/> <!-- Date and time when this data was scrapped from the original website -->
      <actual_datetime_humanIPS val="Mon Mar 18 23:11:45 2024"/> <!-- Date and time when this data was scrapped from the original website, in human readable format -->
      <is_widely_used val="1"/></identification> <!-- 1 if yes, 0 if no: is the document normative and in wide use (see article preprint for the details) -->
    </identification>
    <references>
      <classifierByIPS val="000.000.000.000.000" /> <!-- classification code according to the IPS Zakonodatelstvo -->
    </references>
    <keywords>
      <keywordByIPS val="KEYWORD" /> 
    </keywords>
  </meta>
  <body>
    <textIPS><-- Text parsed from the IPS Zakonodatelstvo --> 
    <!-- It can include hyperlinks to other acts, mostly amendments,
    like this: --> text <ref>linked text</ref> text 
    </textIPS>
    <taggedTextIPS> <-- CONLL_U morphosyntactic tagged text, cleaned -->
    </taggedTextIPS> 
  </body>
</act>
```

## Ограничения
Этот корпус не представляет всей полноты правовых актов, а скорее представляет собой совокупность документов, опубликованных в электронном виде в источнике.

В России не существует единого идентификационного номера правового акта, идентификация может осуществляться по трем признакам в совокупности: официальному номеру документа, дате подписания и государственному органу, принявшему документ. ID Pravo.gov.ru — это внутренний идентификатор базы данных, он не является официальным и может меняться.

Принимаются только первые версии актов (которые изначально были подписаны соответствующим органом). В корпус не включены сводные (с дальнейшими изменениями) тексты, актуальные на настоящее время. Это могло произойти только в том случае, если первоначальные публикации (до 1990 г.) уже включали поправки.

## Использование
На данных корпуса в этой и предыдущих его верисях авторами опубликовано несколько работ.

Saveliev, D. (2018). On creating and using text of the Russian Federation corpus of legal acts acts as open dataset. Pravo. Zhurnal Vysshey shkoly ekonomiki (1), 26–44. DOI: 10.17323/2072-8166.2018.1.26.44 (in Russian). [link](https://law-journal.hse.ru/article/view/20373)

Kuchakov, R. and D. Saveliev (2018). The complexity of the Russian legislation from the lexical and syntactic
perspective (Slozhnost’ pravovyh aktov v Rossii: leksicheskoe i sintaksicheskoe kachestvo tekstov). Analytic report,
IRL European University. [link](https://enforce.spb.ru/images/analit_zapiski/memo_readability_2018_
web.pdf) (in Russian).

Saveliev, D. (2020). Study of the complexity of sentences that make up the texts of legal acts of the authorities of the Russian Federation. Pravo. Zhurnal Vysshey shkoly ekonomiki (1), 50-74. DOI: 10.17323/2072-8166.2020.1.50.74 (in Russian).[link](https://law-journal.hse.ru/article/view/20098)


## Лицензия
Российское законодательство исключает тексты правовых актов из охраны авторским правом, так что они могут свободно распространяться. Открытые данные об официальной публикации имеют свои условия рспространения (коммерческое и некоммерческое использование допускается при условии [ссылки на источник](http://publication.pravo.gov.ru/od/)).

Остальные материалы доступны на условиях лицензии Creative Commons Attribution-NonCommercial 4.0 International license.

## Информация о поддержке
Корпус опубликован в рамках научного проекта No 17-18-01618, поддержанного Российским научным фондом.

## Контакты
[Денис Савельев](http://enforce.spb.ru/about-us/team/6922-savelev-denis-aleksandrovich)([@denissaveliev](https://github.com/denissaveliev)) научный сотрудник Института проблем правоприменения при Европейском университете в Санкт-Петербурге 
