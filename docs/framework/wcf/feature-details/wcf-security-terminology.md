---
title: "Терминология WCF в сфере безопасности | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "безопасность [WCF], терминология"
  - "глоссарий по безопасности [WCF]"
  - "термины в сфере безопасности [WCF]"
ms.assetid: 68dde024-8e51-40ba-804f-ec52d85e9ca9
caps.latest.revision: 14
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 14
---
# Терминология WCF в сфере безопасности
Не все пользователи знакомы с терминологией, которая используется при обсуждении вопросов безопасности.В данном разделе кратко объясняются некоторые термины, относящиеся к безопасности, однако его целью не является исчерпывающее объяснение каждого термина.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] терминах, используемых в документации [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], см. в разделе [Основные понятия Windows Communication Foundation](../../../../docs/framework/wcf/fundamental-concepts.md).  
  
 список управления доступом \(ACL\)  
 Список мер по обеспечению безопасности, применяемый к объекту.\(Объектом может быть файл, процесс, событие или какой\-либо другой объект с дескриптором безопасности.\) Запись в списке ACL представляет собой элемент управления доступом \(ACE\).Существует два типа списков ACL: на уровне пользователя и на уровне системы.  
  
 проверка подлинности  
 Процедура проверки того, что пользователь, компьютер, служба или процесс действительно является тем, за кого себя выдает.  
  
 авторизация  
 Процесс предоставления пользователю прав на выполнение некоторых действий.Например, можно разрешить членам одной группы изменять файл, а членам другой группы — только читать его.  
  
 сертификат центра сертификации \(CA\)  
 Определяет центр сертификации, который выдает сертификаты проверки подлинности сервера и клиента серверам и клиентам, запрашивающим эти сертификаты.Поскольку в сертификате содержится открытый ключ, используемый в цифровых подписях, его также называют *сертификатом сигнатуры*.Если центр сертификации является корневым, сертификат ЦС также называют *корневым сертификатом*.Кроме того, иногда его называют *сертификатом узла*.  
  
 Иерархия ЦС  
 В иерархии ЦС содержится несколько центров сертификации.Она организована таким образом, что каждый ЦС сертифицируется другим ЦС, расположенным на более высоком уровне иерархии, который, в свою очередь, сертифицируется следующим ЦС и т. д.; на самом верхнем уровне иерархии находится *корневой центр*.  
  
 сертификат  
 Документ с цифровой подписью, содержащий информацию о сущности и открытом ключе сущности и связывающий эти данные вместе.Сертификат выдается доверенной организацией, называемой центром сертификации, после подтверждения этим центром подлинности сущности.  
  
 В сертификатах могут содержаться различные типы данных.Например, сертификат X.509 включает формат сертификата, серийный номер сертификата, алгоритм сигнатуры сертификата, имя ЦС, которым был издан сертификат, имя и открытый ключ сущности, запрашивающей сертификат, а также сигнатура центра сертификации.  
  
 хранилище сертификатов  
 Как правило, постоянное хранилище, в котором хранятся сертификаты, списки отзыва сертификатов и списки доверия сертификатов.Тем не менее, при работе с сертификатами, которые не требуется помещать в постоянное хранилище, можно создать и открыть хранилище сертификатов, полностью находящееся в оперативной памяти.  
  
 утверждение  
 Информация, которая передается от одной сущности к другой и используется для установления личности отправителя.Пример: маркер имени пользователя и пароля или сертификат X.509.  
  
 сертификат клиента  
 Сертификат, используемый для проверки подлинности клиента, например для проверки подлинности веб\-браузера веб\-сервером.При попытке доступа веб\-браузера клиента к защищенному веб\-серверу клиент передает серверу свой сертификат, чтобы сервер мог проверить идентификацию клиента.  
  
 учетные данные  
 Предварительно проверенные на подлинность данные для входа в систему, которые участник безопасности использует для собственной идентификации \(например, пароль или билет протокола Kerberos\).Учетные данные используются для контроля доступа к ресурсам.  
  
 данные с хэшем  
 Тип данных содержимого, определенный стандартом PKCS 7 и состоящий из любого типа данных и хэша сообщения содержимого.  
  
 цифровая сигнатура  
 Данные, связывающие личность отправителя с передаваемой информацией.Цифровая сигнатура может включаться в сообщение, файл или другой блок информации, представленной в цифровом виде, либо передаваться отдельно.Цифровые сигнатуры используются в средах открытых ключей и предоставляют возможность проверки подлинности и целостности данных.  
  
 кодирование  
 Процесс преобразования данных в поток битов.Кодирование является частью процесса сериализации, преобразующего данные в поток единиц и нулей.  
  
 пара ключей обмена  
 Пара, состоящая из открытого и закрытого ключей, которая используется для шифрования сеансовых ключей с целью безопасного хранения этих ключей и обмена ими с другими пользователями.  
  
 хэш  
 Числовое значение фиксированного размера, полученное в результате применения математической функции \(см. "хэш\-алгоритм"\) к данным произвольного размера.Данные обычно включают случайную информацию, называемую *специальным словом*.Как служба, так и клиент добавляют специальные слова в процессе обмена для повышения сложности результата.Этот результат называется *хэшем*.Передача хэш\-значения безопаснее передачи конфиденциальных данных, таких как пароль, даже если он зашифрован.Отправитель и получатель хэша должны предварительно согласовать хэш\-алгоритм и специальные слова, чтобы обеспечить возможность проверки полученного хэша.  
  
 хэш\-алгоритм  
 Алгоритм, используемый для получения хэш\-значения некоторого блока данных, например сообщения или сеансового ключа.К типичным хэш\-алгоритмам относятся MD2, MD4, MD5 и SHA\-1.  
  
 Протокол Kerberos  
 Протокол, определяющий порядок взаимодействия клиентов с сетевой службой проверки подлинности.Клиенты получают билеты в центре распространения ключей Kerberos и предъявляют их серверам при установлении соединений.Билеты Kerberos представляют собой сетевые учетные данные клиента.  
  
 подсистема LSA  
 Защищенная подсистема, выполняющая проверку подлинности пользователей и разрешающая им вход в локальную систему.В подсистеме LSA также хранятся сведения о всех аспектах безопасности локальной системы, которые в совокупности называются локальной политикой безопасности системы.  
  
 Negotiate  
 Поставщик поддержки безопасности \(SSP\), выступающий в качестве уровня приложения между интерфейсом поставщика поддержки безопасности \(SSPI\) и другими поставщиками SSP.Когда приложение обращается к интерфейсу SSPI для выполнения входа в сеть, оно может указать SSP для обработки запроса.Если приложение указывает `Negotiate`, `Negotiate` анализирует запрос и выбирает оптимального поставщика SSP для обработки запроса на основе политики безопасности, настроенной пользователем.  
  
 специальное слово  
 Случайное значение, используемое для предотвращения атак воспроизведения.  
  
 неотрекаемость  
 Невозможность отказа пользователя от факта выполнения им определенных действий.Например, при каждом удалении пользователем какого\-либо файла система может записывать в журнал идентификатор этого пользователя.  
  
 стандарт PKCS  
 Спецификации от компании RSA data Security, Inc.совместно с различными разработчиками защищенных систем, чтобы расширить применение асимметричного шифрования.  
  
 PKCS 7  
 Стандарт Cryptographic Message Syntax.Определяет общий синтаксис для данных, к которым могут применяться криптографические функции, например цифровая сигнатура и шифрование.Также определяет синтаксис для распространения сертификатов или списков отзыва сертификатов и других атрибутов сообщений, таких как отметки времени.  
  
 открытый текст  
 Сообщение в незашифрованном виде.Незашифрованные сообщения также называют сообщениями *с открытым текстом*.  
  
 привилегия  
 Право пользователя выполнять различные системные операции, такие как завершение работы системы, загрузка драйверов устройств или изменение системного времени.В маркере доступа пользователя содержится список привилегий, которыми располагает пользователь или группа пользователя.  
  
 закрытый ключ  
 Секретная часть пары ключей, используемой в алгоритме асимметричного шифрования.Закрытые ключи обычно используются для шифрования симметричных сеансовых ключей, создания цифровой подписи сообщения или расшифрования сообщения, зашифрованного с помощью соответствующего открытого ключа.См. также "открытый ключ".  
  
 процесс  
 Контекст безопасности, в рамках которого выполняется приложение.Как правило, контекст безопасности связывается с пользователем, поэтому все приложения, выполняющиеся в рамках заданного процесса, получают разрешения и привилегии владеющего пользователя.  
  
 пара открытого и закрытого ключей  
 Набор ключей шифрования, используемых в алгоритмах асимметричного шифрования.Для каждого пользователя поставщик служб шифрования обычно предоставляет две пары открытого и закрытого ключей: пару ключей обмена и пару ключей цифровой сигнатуры.Обе пары сохраняются от сеанса к сеансу.  
  
 открытый ключ  
 Ключ шифрования, который обычно используется для расшифрования сеансового ключа или цифровой сигнатуры.Открытый ключ также можно использовать для зашифрования сообщения, которое сможет расшифровать только владелец соответствующего закрытого ключа.  
  
 асимметричное шифрование  
 Способ шифрования, в котором используется пара ключей; один ключ используется для зашифрования данных, а другой — для их расшифрования.В противоположность этому в алгоритмах симметричного шифрования для зашифрования и расшифрования данных используется один и тот же ключ.На практике алгоритм асимметричного шифрования обычно применяется для защиты сеансового ключа, используемого алгоритмом симметричного шифрования.В этом случае открытый ключ используется для зашифрования сеансовым ключом, который, в свою очередь, используется для шифрования некоторых данных, а закрытый ключ используется для расшифрования ключа сеанса.Кроме защиты сеансовых ключей алгоритмы асимметричного шифрования можно также использовать для создания сигнатуры сообщения \(с помощью закрытого ключа\) и проверки сигнатуры \(с помощью открытого ключа\).  
  
 инфраструктура открытых ключей \(PKI\)  
 Инфраструктура, предоставляющая комплексный набор служб и средств администрирования для создания, развертывания и управления приложениями, реализующими асимметричное шифрование.  
  
 отказ  
 Способность пользователя ложно опровергнуть факт выполнения им определенного действия, когда другие стороны не могут доказать, что он его выполнял.Пример: пользователь удалил файл и может успешно опровергнуть факт удаления им этого файла.  
  
 корневой центр  
 Центр сертификации, расположенный на самом верхнем уровне иерархии ЦС.Корневой центр сертифицирует центры сертификации, расположенные на следующем уровне иерархии.  
  
 алгоритм SHA  
 Хэш\-алгоритм, формирующий хэш.SHA используется в различных алгоритмах; в частности, он используется совместно с алгоритмом DSA в алгоритме DSS.Существует четыре разновидности алгоритма SHA: SHA\-1, SHA\-256, SHA\-384 и SHA\-512.SHA\-1 формирует хэш\-значение длиной 160 бит.SHA\-256, SHA\-384 и SHA\-512 формируют хэш\-значения длиной 256, 384 и 512 бит соответственно.Алгоритм SHA был разработан специалистами Национального института стандартов и технологий США \(NIST\) и Агентства национальной безопасности США \(NSA\).  
  
 протокол SSL  
 Протокол, обеспечивающий безопасное сетевое взаимодействие с использованием комбинации технологий шифрования с открытым и секретным ключом.  
  
 контекст безопасности  
 Атрибуты безопасности или правила, применяемые в текущий момент времени.Пример: текущий пользователь, вошедший в систему, или персональный идентификационный номер, введенный пользователем смарт\-карты.В случае интерфейса SSPI контекстом безопасности является непрозрачная структура данных, в которой содержатся данные безопасности, относящиеся к соединению, например сеансовый ключ или значение продолжительности сеанса.  
  
 участник безопасности  
 Сущность, распознаваемая системой безопасности.Участниками могут являться пользователи, а также автономные процессы.  
  
 поставщик поддержки безопасности \(SSP\)  
 Библиотека динамической компоновки \(DLL\), реализующая интерфейс SSPI путем обеспечения доступности приложениям одного или нескольких пакетов безопасности.Каждый пакет безопасности обеспечивает сопоставление вызовов функций интерфейса SSPI приложения и вызовов функций фактической модели безопасности.Пакеты безопасности поддерживают такие протоколы, как проверка подлинности Kerberos и Microsoft LAN Manager \(LanMan\).  
  
 интерфейс поставщика поддержки безопасности \(SSPI\)  
 Обычный интерфейс между приложениями транспортного уровня, такими как Microsoft RPC, и поставщиками безопасности, такими как Windows Distributed Security.Интерфейс SSPI позволяет приложению транспортного уровня вызвать один из нескольких поставщиков безопасности для получения соединения, прошедшего проверку подлинности.Для выполнения таких вызовов не требуются глубокие знания протоколов безопасности.  
  
 служба маркеров безопасности  
 Службы, предназначенные для выдачи пользовательских маркеров безопасности и управления ими в сценарии с несколькими службами.Пользовательские маркеры обычно являются маркерами SAML, включающими пользовательские учетные данные.  
  
 сертификат сервера  
 Сертификат, используемый для проверки подлинности сервера, например для проверки подлинности веб\-сервера веб\-браузером.При попытке доступа веб\-браузера клиента к защищенному веб\-серверу сервер передает браузеру свой сертификат, чтобы браузер мог проверить идентификацию сервера.  
  
 сеанс  
 Обмен сообщениями под защитой единого ключевого материала.Например, в сеансах SSL используется единый ключ для защиты нескольких сообщений, передаваемых в прямом и обратном направлениях.  
  
 сеансовый ключ  
 Случайный ключ, который используется однократно, а затем удаляется.Сеансовый ключ являются симметричными \(используются как для зашифрования, так и для расшифрования\).Они передаются вместе с сообщением, защищенным посредством шифрования с помощью открытого ключа законного получателя сообщения.Сеансовый ключ представляет собой случайное число длиной приблизительно от 40 до 2000 бит.  
  
 дополнительные учетные данные  
 Учетные данные, используемые для прохождения проверки подлинности участника безопасности во внешних доменах безопасности.  
  
 симметричное шифрование  
 Способ шифрования, в котором для зашифрования и расшифрования используется один и тот же ключ.Симметричное шифрование используется при шифровании больших объемов данных.К наиболее распространенным алгоритмам симметричного шифрования относятся RC2, RC4 и DES.  
  
 См. также "асимметричное шифрование".  
  
 симметричный ключ  
 Ключ, используемый как для зашифрования, так и для расшифрования.Сеансовый ключ, как правило, являются симметричными.  
  
 маркер \(маркер доступа\)  
 В маркере доступа содержится информация, относящаяся к безопасности, для сеанса входа в систему.Система создает маркер доступа при входе пользователя в систему, и каждый процесс, выполняемый от имени пользователя, имеет копию этого маркера.Маркер определяет пользователя, а также его группы и привилегии.Система использует маркер для управления доступом к защищаемым объектам и контроля способности пользователя выполнять различные системные операции на локальном компьютере.Предусмотрено два типа маркеров доступа: основной маркер и маркер олицетворения.  
  
 транспортный уровень  
 Сетевой уровень, отвечающий за качество обслуживания и доставку данных без ошибок.К задачам, выполняемым на этом уровне, относятся обнаружение и коррекция ошибок.  
  
 список доверия сертификатов  
 Предварительно определенный список элементов, подписанный доверенной сущностью.Список доверия сертификатов может быть представлен в произвольной форме, например, он может быть задан в виде списка хэш\-значений сертификатов или списка имен файлов.Все элементы списка прошли проверку подлинности \(утверждены\) подписывающей сущностью.  
  
 поставщик доверия  
 Программное обеспечение, определяющее, можно ли доверять заданному файлу.Решение принимается на основе сертификата, связанного с файлом.  
  
 имя участника\-пользователя  
 Имя учетной записи пользователя \(которое иногда называют *именем для входа в систему*\) и имя домена, определяющее домен, в котором располагается учетная запись пользователя.Это стандартный способ входа в домен Windows.Используется следующий формат: someone@example.com \(аналогично адресу электронной почты\).  
  
> [!NOTE]
>  Помимо имен участников\-пользователей в стандартной форме [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] принимает имена участников\-пользователей в форме нижнего уровня, например cohowinery.com\\someone.  
  
 X.509  
 Международный стандарт сертификатов, определяющий их обязательные части.  
  
## См. также  
 [Основные понятия Windows Communication Foundation](../../../../docs/framework/wcf/fundamental-concepts.md)   
 [Основные понятия безопасности](../../../../docs/framework/wcf/feature-details/security-concepts.md)   
 [Модель безопасности для Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x419)