# Гайд по шаблону

## Методология
В проекте используется методология FSD - в последнее время довольно популярная. Проект состоит из папок с разным уровнем ответсвенности: app, pages, widgets, features, entities, shared
Подробнее далее...

### App
Согласно методолгии, app - папка, в которой находятся структуры, используемые во всем приложении. Ровно это и там и находится
// src/app
-providers
--ErrorBoundary
--StoreProvider
--router

-styles
--providers
--themes
--globalStyles.ts

-types

#### Providers
Там самые нужные провайдеры, котоыре нужны на начальном этапе разработки приложения: ErrorBoundary - ловим ошибки, StoreProvider - организация RTK, router - организация react-router-dom

#### Styles
Организация styled-components - темы, глобальные стили, удобная работа с библиотекой для комфортной разработки

#### Pages
Страницы вашего приложения, в шаблоне главная и Not Found 404 - считаю для начала этого достаточно, можно было бы добавить страницу с ошибкой, но она слишком специфична по логике, ее только самому и писать

# Widgets 
Собрал там основные компоненты для страницы - Page, PageLoader, PageError. Page - тот же main, но с опциональной логикой функцией сохранения скролла при редиректе

### Features 
Продолжение тем, языков и UI слой для сохранения состояния скролла и темы - очень гибкий раздел, его можно использовать повсюду, поэтому в Entities, причем он достаточно тематичен, чтобы не быть в Shared

### Entities
Там только сущность пользователя и Auth. Есть сразу авторизация, аутентификая, 0Auth2.0 от Гугла, Гитхаба, ВК, Дискорда, Яндекса - выбирайте

### Shared
структура:
-api

-config
--i18n

-consts

-lib
--components/DynamicModuleLoader
--hooks
--store 

-types

-ui
--AppImage
--Loader
--Portal
--Stack (Flex, HStack, VStack)

#### i18n 
i18n полностью настроенный, в public можно писать переводы в en и ru json-файлы

#### lib
DynamicModuleLoader - ленивая загрузка слайсов RTK 

hooks - собрание жизненно необходимых хуков: useAppDispatch, useAppSelector - от RTK, useInitialEffect, useDebounce, useThrottling, useInfiniteScroll, useHover, useDispatchedActions

store - buildSelector и buildSlice являются невероятно полезными надстойками над RTK. благодаря buildSlice можно не использовать useDispatch 90% разработки, всю работу делает хук внутри. я, когда писал это, в таком восторге был, надеюсь, вы тоже

#### UI
Самые необходимые (кроме Loader) компоненты, которые серьезно помогают в разработке. HSatck и VStack - flex-контейнеры с flex-direction row и column соответственно


