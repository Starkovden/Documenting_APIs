# Обзор руководства OpenAPI 3.0

В этом разделе мы углубимся в спецификацию OpenAPI. Мы будем использовать тот же [API-интерфейс OpenWeatherMap](https://openweathermap.org/current), который мы использовали в других частях этого курса, в качестве контента для нашего документа OpenAPI. Используя этот API, мы создадим действительный документ спецификации OpenAPI, а затем изобразим его в интерактивной документации используя Swagger UI.

[Общие ресурсы для изучения спецификации OpenAPI](#general)

[Чем отличается руководство по OpenAPI/Swagger Тома Джонсона](#tutorialDiff)

[Терминология Swagger и OpenAPI](#terminology)

[Начнем с общего представления](#bigPicture)

[Учебник OpenAPI шаг за шагом](#follow)

[Миграция от OpenAPI 2.0 к 3.0](#migration)

[Полезные источники](#resources)

<a name="general"></a>
## Общие ресурсы для изучения спецификации OpenAPI

Изучение [спецификации OPenAPI](https://github.com/OAI/OpenAPI-Specification) займет какое-то время. В качестве оценки планируйте около двух недель погружения, работая с конкретным API в контексте спецификации, прежде чем освоиться с ним. По мере изучения спецификации OpenAPI используйте следующие ресурсы:

- [Образцы документов спецификации OpenAPI](https://github.com/OAI/OpenAPI-Specification/tree/master/examples/v3.0). Эти образцы документов спецификации являются хорошей отправной точкой в ​​качестве основы для документации спецификации. Они дают общее представление об общей форме документа спецификации.
- [Руководство пользователя Swagger](https://swagger.io/docs/specification/about/). Руководство пользователя Swagger дружелюбное, концептуальное и легкое для понимания. В нем нет детализации и точности документации по спецификации на GitHub, но во многих отношениях она более понятна и содержит больше примеров.
- [Документация по спецификации OpenAPI](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md). Техническая документация является технической и требует некоторого привыкания, но мы, несомненно, будем часто к ней обращаться при описании своего API. Это длинный одностраничный документ, искать можно с помощью `Ctrl+F`.

> В Интернете есть другие учебные пособия по Swagger / OpenAPI, но обязательно следуйте [учебным пособиям для версии 3.0 API](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md), а не [2.0](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md). Версия 3.0 была [выпущена в июле 2017 года](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md#appendix-a-revision-history). 3.0 существенно отличается от 2.0. ([Версия 3.0.2](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md) была выпущена в декабре 2017 года и внесла незначительные улучшения в версию 3.0. Обратите внимание, что всякий раз, при ссылке на 3.0, имеется в виду 3.x, что означает любой инкрементный выпуск точек из строки 3.0.)

<a name="tutorialDiff"></a>
## Чем отличается руководство по OpenAPI/Swagger Тома Джонсона

Можно найти много учебных пособий по Swagger онлайн. В чем отличие этого руководства? Помимо сквозного пошагового руководства, использующего версию спецификации OpenAPI 3.0 (а не 2.0), и фактического API для контекста, здесь показано, как поля OpenAPI отображаются в пользовательском интерфейсе Swagger. В частности, демонстрируется, как и где каждое из полей OpenAPI отображается в Swagger UI.

Конечно, многие другие фрэймворки могут анализировать и отображать информацию в документе спецификации OpenAPI, но [Swagger UI](https://github.com/swagger-api/swagger-ui) является одним из самых популярных. Swagger UI спонсируется SmartBear, той же компанией, которая активно инвестирует в [инициативу OpenAPI](https://www.openapis.org/) и разрабатывает [Swaggerhub](https://github.com/Starkovden/Documenting_APIs/blob/master/4.%20OpenAPI%20specification%20and%20Swagger/4.16.%20SwaggerHub%20introduction%20and%20tutorial.md). Их Инструментарий почти всегда синхронизирован с новейшими разработками. Swagger UI - активно разработанный и управляемый опен-сорс проект.

Показывая, как поля в спецификации отображаются в пользовательском интерфейсе Swagger, Том Джонсон надеется, что объекты и свойства спецификации приобретут большую актуальность и значение. Отображение пользовательского интерфейса Swagger - это всего лишь *одна из возможностей* визуального отображения информации о спецификации.

<a name="terminology"></a>
## Терминология Swagger и OpenAPI

Прежде чем продолжить, уточним некоторые термины для тех, кто может быть незнаком с OpenAPI/Swagger:

- [Swagger](https://swagger.io/) был оригинальным названием спецификации OpenAPI, но позже спецификация была изменена на [OpenAPI](https://github.com/OAI/OpenAPI-Specification/), чтобы усилить открытую, непатентованную природу этого стандарта. Теперь «Swagger» относится к инструментам API, которые поддерживают спецификацию OpenAPI, а не к самой спецификации. Люди по-прежнему часто ссылаются на оба имени взаимозаменяемо, но «OpenAPI» - это то, как следует обращаться к спецификации.
- [Smartbear](https://smartbear.com/) - это компания, которая поддерживает и разрабатывает инструменты Swagger с открытым исходным кодом (Swagger Editor, Swagger UI, Swagger Codegen и другие). Они не владеют [спецификацией OpenAPI](https://github.com/OAI/OpenAPI-Specification/), так как Linux Foundation поддерживает эту [инициативу](https://www.openapis.org/). Разработка спецификации OpenAPI ведется [многими компаниями и организациями](https://www.openapis.org/membership/members).
- «Документ спецификации OpenAPI» или «документ OpenAPI» - это Swagger-файл в формате YAML, который создается для описания API.

Другие определения находятся в [Глоссарии API](https://github.com/Starkovden/Documenting_APIs/blob/master/10.%20API%20glossary%20and%20Resourses/10.1.%20Glossary%20for%20API%20documentation.md)

Разберемся с некоторыми дополнительными дескрипторами JSON и YAML. Документ спецификации в моем руководстве по OpenAPI использует YAML (который вкратце представлен [здесь](https://github.com/Starkovden/Documenting_APIs/blob/master/4.%20OpenAPI%20specification%20and%20Swagger/4.3.%20Working%20in%20YAML.md)), но он также может быть создан и в JSON. JSON - это подмножество YAML, поэтому эти два формата являются практически взаимозаменяемыми (для структур данных, которые мы используем). В конечном счете, однако, спецификация OpenAPI является объектом JSON. Примечания к спецификации:

> Документ OpenAPI, который соответствует Спецификации OpenAPI, сам по себе является объектом JSON, который может быть представлен в формате JSON или YAML. (См. [Format](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md#format))

Другими словами, созданный документ OpenAPI является объектом JSON, но у нас есть возможность выразить JSON с использованием синтаксиса JSON или YAML. YAML более читабелен и является более распространенным форматом (см. Обсуждение API Handyman [JSON против YAML](https://apihandyman.io/writing-openapi-swagger-specification-tutorial-part-1-introduction/#json-vs-yaml)), поэтому YAML используется только здесь. Документация спецификации OpenAPI на GitHub всегда показывает синтаксис JSON и YAML при отображении форматов спецификации. (Для более подробного сравнения YAML с JSON см. «Отношение к JSON» в [спецификации YAML](https://yaml.org/spec/1.2/spec.html).)

YAML относится к структурам данных с тремя основными терминами: маппинг (отображения) (хэши / словари), последовательности (массивы / списки) и скаляры (строки / числа)» (см. «Введение» в [YAML 1.2](https://yaml.org/spec/1.2/spec.html)). Однако, поскольку спецификация OpenAPI является объектом JSON, он использует терминологию JSON - например, «объекты», «массивы», «свойства», «поля» и так далее. Поэтому содержимое будет показываться в формате YAML, но описываться будет с помощью терминологии JSON.

Каждый уровень в YAML (определенный отступом в два пробела) является объектом. В следующем коде `california` является объектом. `animal`, `flower` и `bird`  являются свойствами объекта `california`.

    california:
      animal: Grizzly Bear
      flower: Poppy
      bird: Quail

В JSON это выглядит так:

    {
        "california": {
            "animal": "Grizzly Bear",
            "flower": "Poppy",
            "bird": "Quail"
        }
    }


В спецификации часто используется термин «поле» в заголовках и именах столбцов таблицы при перечислении свойств для конкретного объекта. (Кроме того, идентифицируется два типа полей: объявляются «фиксированные» поля, уникальные имена, а «шаблонные» поля являются выражениями регулярных выражений.) `Поля` и `свойства` используются в спецификации OpenAPI как синонимы.

В коде ниже `countries` содержит объект с именем `united_states`, который содержит объект с именем `california`, который содержит несколько свойств со строковыми значениями:

    countries:
      united_states:
        california:
          animal: Grizzly Bear
          flower: Poppy
          bird: Quail

Ниже пример объекта `demographics`, содержащего массив:

    demographics:
      - population
      - land
      - rivers

И вот как он выглядит в JSON:

    {
        "demographics": [
            "population",
            "land",
            "rivers"
        ]
    }

Надеемся, что эти краткие примеры помогут понять терминологию, использованную в руководстве.

<a name="bigPicture"></a>
## Начнем с общего представления

Если вы хотите получить общее представление о спецификации, взгляните на [примеры 3.0 здесь](https://github.com/OAI/OpenAPI-Specification/tree/master/examples/v3.0), в частности [спецификацию Petstore OpenAPI](https://github.com/OAI/OpenAPI-Specification/blob/master/examples/v3.0/petstore.yaml). Поначалу, вероятно, будет много непонятного, но постараемся получить представление о целом, прежде чем мы углубимся в детали. Посмотрим также на некоторые другие примеры в папке v.3.0.

<a name="follow"></a>
## Учебник OpenAPI шаг за шагом

Пошаговое руководство OpenAPI состоит из 8 шагов. Каждый шаг соответствует одному из объектов корневого уровня в документе OpenAPI.

- [Шаг 1 объект `openapi`](https://github.com/Starkovden/Documenting_APIs/blob/master/4.%20OpenAPI%20specification%20and%20Swagger/4.5.%20Step%201%20The%20openapi%20object.md)
- [Шаг 2 объект `info`](https://github.com/Starkovden/Documenting_APIs/blob/master/4.%20OpenAPI%20specification%20and%20Swagger/4.6.%20Step%202%20The%20info%20object.md)
- [Шаг 3 объект `servers`](https://github.com/Starkovden/Documenting_APIs/blob/master/4.%20OpenAPI%20specification%20and%20Swagger/4.7.%20Step%203%20The%20servers%20object.md)
- [Шаг 4 объект `paths`](https://github.com/Starkovden/Documenting_APIs/blob/master/4.%20OpenAPI%20specification%20and%20Swagger/4.8.%20Step%204%20The%20paths%20object.md)
- [Шаг 5 объект `components`](https://github.com/Starkovden/Documenting_APIs/blob/master/4.%20OpenAPI%20specification%20and%20Swagger/4.9.%20Step%205%20The%20components%20object.md)
- [Шаг 6 объект `security`](https://github.com/Starkovden/Documenting_APIs/blob/master/4.%20OpenAPI%20specification%20and%20Swagger/4.10.%20Step%206%20security%20object.md)
- [Шаг 7 объект `tags`](https://github.com/Starkovden/Documenting_APIs/blob/master/4.%20OpenAPI%20specification%20and%20Swagger/4.11.%20Step%207%20The%20tags%20object.md)
- [Шаг 8 объект `externalDocs`](https://github.com/Starkovden/Documenting_APIs/blob/master/4.%20OpenAPI%20specification%20and%20Swagger/4.12.%20Step%208%20The%20externalDocs%20object.md)

Не обязательно создавать документ спецификации в этом порядке; порядок выбран, чтобы предоставить более конкретный путь и шаги к процессу.

В следующих разделах мы рассмотрим каждый из этих объектов один за другим и задокументируем текущий [API OpenWeatherMap](https://openweathermap.org/current). Работа с каждым объектом корневого уровня индивидуально (а не документирование всего сразу) помогает уменьшить сложность спецификации.

> `components` - это скорее объект хранения схем, определенных в других объектах, но чтобы избежать одновременного введения слишком большого количества данных, подождем, пока в руководстве `components` не будет полностью объяснено, как ссылаться на схему в одном объекте (используя `$ref`), который указывает на полное определение в `components`.

С каждым шагом мы будем вставлять объект, над которым работаем, в редактор Swagger. На правой панели редактора Swagger будет отображаться интерфейс Swagger. (Помните, что один документ спецификации ничего не делает с вашим контентом. Для чтения и отображения документа спецификации требуются другие инструменты.)

Позже, когда мы узнаем больше о публикации документации, будет пояснение, как сконфигурировать интерфейс Swagger с нашим документом спецификации в качестве отдельного продукта. Для нашего примера API OpenWeatherMap вы можете увидеть спецификацию OpenAPI, отображаемую интерфейсом Swagger, по следующим ссылкам:

- [Standalone Swagger UI with OpenWeatherMap API](https://idratherbewriting.com/learnapidoc/assets/files/swagger/)
- [Embedded Swagger with OpenWeatherMap API](https://github.com/Starkovden/Documenting_APIs/blob/master/4.%20OpenAPI%20specification%20and%20Swagger/4.15.%20Swagger%20Ui%20demo.md)

<a name="migration"></a>
## Миграция от OpenAPI 2.0 к 3.0

При наличии существующего документа спецификации, который проверяется на соответствие версии OpenAPI 2.0 и можно конвертировать его в OpenAPI 3.0 (или наоборот), можно использовать  [APIMATIC's Transformer](https://www.apimatic.io/transformer) для его автоматического преобразования. (Можно использовать APIMATIC для преобразования документа спецификации во многие другие выходные данные, такие как [RAML](https://github.com/Starkovden/Documenting_APIs/blob/master/10.%20API%20glossary%20and%20Resourses/10.6.%20RAML%20tutorial.md), [API Blueprint](https://github.com/Starkovden/Documenting_APIs/blob/master/10.%20API%20glossary%20and%20Resourses/10.7.%20API%20Blueprint%20tutorial.md) или [Postman](https://github.com/Starkovden/Documenting_APIs/blob/master/2.%20Using%20an%20API%20like%20a%20developer/2.3.%20Submit%20requests%20through%20Postman.md).)

Чтобы увидеть разницу между версиями 2.0 и 3.0, можно скопировать примеры кода в отдельные файлы, а затем использовать приложение [Diffmerge](https://sourcegear.com/diffmerge/), чтобы выделить различия. В блоге Readme.io есть хорошая публикация: [A Visual Guide to What’s New in Swagger 3.0](https://blog.readme.io/an-example-filled-guide-to-swagger-3-2/)

<a name="resources"></a>
## Полезные источники

Приступая к созданию файла спецификации OpenAPI, может пригодиться запись [презентации Swagger / OpenAPI Питера Грюнбаума](http://www.stc-psc.org/event/documenting-web-apis-with-swagger-free-webinar/), а также его [курс на Udemy](https://www.udemy.com/learn-swagger-and-the-open-api-specification/).

Приготовились! Сейчас начнем узнавать, насколько мы готовы к техническому написанию API.