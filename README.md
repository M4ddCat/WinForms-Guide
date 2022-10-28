# WinForms-Guide
Как сделать приложение на Windows Forms с использованием Entity Framework и LINQ
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/title.png)
<br/>

# Создание проекта из шаблона
Нужно создать приложение Windows Forms с использованием .NET Framework (НЕ .NET Core (на нём делать дольше))
<br/>
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/1.png)
<br/>
Задаём наше название проекта в поле «Имя проекта», выбираем расположение, и выбираем платформу .NET Framework 4.8. Если этой платформы нет, то версию ниже.
<br/>
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/2.png)
<br/>
# Добавление EDMX модели базы данных
В начале разработки программы нужно создать модель для взаимодействия с нашей базой данных.
Для этого создадим папку (Пкм по нашему проекту), и назовём её «Model».
<br/>
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/3.png)
<br/>
В дальнейшем будет создано множество других папок, делается это для удобства использования, а так-же за это выдаются дополнительные баллы за грамотную структуру проекта.
Далее нужно создать EDMX модель. Для этого создаём новый элемент в папке Model
<br/>
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/4.png)
<br/>
В открывшемся окне выбираем вкладку «Данные», в котором нужно выбрать «Модель ADO.NET EDM», назовём её «Model»
<br/>
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/5.png)
<br/>
Откроется окно «Мастер моделей EDM». В нём выбираем «Конструктор EF из базы данных» и жмём далее
<br/>
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/6.png)
<br/>
В следующем окне нужно создать соединение к нашей базе данных. Для этого нужно нажать на кнопку «Создать соединение…»
<br/>
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/7.png)
<br/>
Вводим имя сервера в поле «Имя сервера» 
Его можно посмотреть в MS SQL Server Management Studio
<br/>
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/8.png)
<br/>
И имя базы данных, которую мы создавали на сервере
<br/>
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/9.png)
<br/>
Жмём «Проверить подключение», чтобы проверить, правильно ли мы ввели названия сервера и базы данных.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/10.png)
<br/>
При успешной проверке закрываем открывшееся окно и жмём ОК.
У нас появилось подключение к базе данных. Нужно поставить галочку на параметре «Сохранить параметры соединения в App.Config…» и нажать «Далее»
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/11.png)
<br/>
Выбираем версию EF 6.x и жмём Далее
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/12.png)<br/>
В следующем окне выбираем все объекты, которые нужно включить в модель, если нужно меняем название, и жмём Готово
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/13.png)<br/>

В папке Model появилась наша EDMX модель, которую мы будем использовать, когда будем взаимодействовать с данными из базы данных.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/14.png)<br/>
# Создание форм
Для начала создадим отдельную папку для форм, аналогично, как мы создавали папку «Model». Назовём её «Forms», и добавим в неё стандартную форму под названием «TemplateForm».
В свойствах ищем вкладку «Стиль окна», и задаём в ней нашу иконку в подпункте Icon, и поменять шрифт на тот, что указан в ТЗ
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/15.png)<br/>
Далее нужно перейти к коду формы. Для этого нужно нажать пкм по форме и выбрать «Перейти к коду».
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/16.png)<br/>
Здесь мы после строки «InitializeComponent();» добавляем «this.Text = “Beauty saloon”;»
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/17.png)<br/>
Данная строка изменяет свойство Text у формы, которое выступает в роли названия окна при открытии.
Это нужно, чтобы наследовать данную форму другими формами, чтобы не пришлось каждый раз задавать иконку и менять текст названия окна.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/18.png)<br/>
# Авторизация
Для авторизации нужно создать подобную форму, а так-же на будущее нужно создать форму MainForm (не забываем, что создаём формы в специально созданной для этого папке) -
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/19.png)<br/>
После создания формы удалим стандартную созданную форму, которая расположена в корне проекта, а именно Form1
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/20.png)<br/>

После удаления нужно открыть файл Program.cs, и изменить в нём запускаемую по умолчанию форму на нашу форму авторизации.
Вернёмся к нашей форме авторизации, и настроим некоторые компоненты.
Для TextBox-а пароля нужно задать параметр UseSystemPasswordChar - True
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/21.png)<br/>
Label расположенный между полем для ввода пароля и кнопкой входа должен быть с параметром Visible – False, и должен отображаться только при условии, что капча была введена неправильно.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/22.png)<br/>
Дальше нужно добавить обработчик нажатия кнопки, для этого жмём на кнопку 2 раза.
В логике обработчика нажатия нужно добавить проверку на наличие введённым пользователем данных в базе данных.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/23.png)<br/>
Сперва нужно добавить контекст базы данных. Чтобы это сделать надо импортировать нашу модель в класс формы. Прописываем почти в самом верху следующую конструкцию - «using НазваниеПроекта.Model;»
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/24.png)
Далее нужно создать объект контекста базы данных. Сделаем это в начале класса.
А так-же создадим наследование от TemplateForm заменив после двоеточия объект Form на нашу форму.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/25.png)
Посмотреть как называется ваш контекст можно в файле «НазваниеВашейМодели.Context.cs», который лежит в «НазваниеВашейМодели.Context.tt»
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/26.png)
Т.к. в изначальном проекте не предусмотрена авторизация, нам самим придётся добавить таблицу в базу данных. Создадим в нашей базе новую таблицу «Users», и зададим в ней следующие поля -
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/27.png)
Так-же нужно добавить несколько собственных значений, чтобы можно было ими воспользоваться при авторизации.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/28.png)
После чего нужно обновить нашу модель EDMX в проекте. Для этого заходим в edmx файл нашей модели, жмём на свободном пространстве и выбираем «Обновить модель из базы данных». 
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/29.png)
Откроется окно «Мастер обновления». В нём ставим галочку в поле «Таблицы» и жмём готово.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/30.png)
После этого модель базы данных обновится, и можно будет взаимодействовать с таблицей «Users”.
После этого создадим условие в обработчике нажатия на кнопку авторизации.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/31.png)
В нём мы используем запрос к таблице Users через созданный нами контекст. В этом запросе мы используем метод расширения Any(), который проверяет есть ли в таблице сущности соответствующие условию. Условие реализовано через лямбда выражение, в котором сравниваются поля из таблицы и текст, который ввёл пользователь на форме.
# Капча, пример её реализации
В экзамене есть критерий реализации капчи. При наличии навыков работы со строчными типами данных она делается довольно быстро, и за счёт этого можно легко получить баллы из-за её наличия.
Сначала нужно создать форму, по типу как на скриншоте, и добавить обработчик нажатия на кнопку.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/32.png)
Создадим функцию getCaptcha, которая будет возвращать string переменную со случайными символами. Получать она будет int значение, которое будет являться длинной капчи.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/33.png)
Название функции выделено красным, потому-что функция ничего не возвращает.
Для начала определим символы, которые будут использоваться при генерации капчи.
Не нужно вводить символы в алфавитном порядке, достаточно их наличие, поэтому проще всего пройтись по символам на клавиатуре.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/34.png)
После чего нужно создать string переменную с пустым значением (“string.Empty”)
Далее используя псевдорандомный генератор чисел (Random( )) и цикл for мы случайным образом получаем буквы из нашей переменной с символами. И сразу-же после цикла мы сделаем конструкцию “return StringVal”, которая будет возвращать string переменную со сгенерированными символами при вызове функции.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/35.png)
Полная часть кода генерации капчи:
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/36.png)
Задействуем эту функцию при вызове формы, чтобы капча выводилась в label
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/37.png)

Добавим обработчик нажатия на кнопку, который будет сравнивать текст введённый в textBox и текст, который записан в label.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/38.png)
DialogResult нужен, чтобы вернуть в форму, из которой мы вызвали эту форму результат завершения этой формы.
В коде авторизации добавим вызов капчи, для этого создадим новый объект класса формы капчи, и вызовем его как диалог, чтобы нельзя было взаимодействовать с формой авторизации, при этом создав новый объект типа DialogResult, чтобы можно было вернуть из этого диалога какой-то результат. 
Допишем обработчик завершения формы, т. к. код написанный после вызова диалога выполняется только после завершения диалога. В нём вызываем основную форму, и скрываем форму авторизации, если результат формы с капчей был «ОК», иначе ставим видимость label с текстом, показывающим, что пользователь ввёл капчу неправильно на true. 
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/39.png)
# Основная форма
Согласно ТЗ нам нужно сделать вывод данных из таблицы. Необходимо, чтобы эти данные можно было фильтровать, а так-же, чтобы можно было просматривать данные по количеству строк, которые выберет пользователь.
Создадим следующую форму, на которой в качестве объекта в который будут выводиться данные будет выступать dataGridView. Так-же сразу-же добавим элементы для сортировки данных, которые будут выводиться в таблицу, и кнопки, которые понадобятся позже, для взаимодействия с данными.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/40.png)
После того, как создали все объекты на форме нужно нажать на саму форму 2 раза, чтобы создался обработчик загрузки формы.
В нём нужно сразу прописать «ClientGridView.SelectionMode = DataGridViewSelectionMode.FullRowSelect;», чтобы в dataGridView выбор был не по клетке, а сразу по строке.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/41.png)
Здесь-же нужно создать несколько массивов string значений, которые будут использоваться для выбора параметров фильтрации.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/42.png)
Эти массивы мы используем как источник данных для SelectBox-ов.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/43.png)
Заранее определим выбранный индекс этих SelectBox-ов, при помощи метода расширения SelectedIndex, который принимает только int-овые значения.
Так-же т. к. мы будем взаимодействовать с нашей базой данных, добавляем импорт edmx модели, созданной ранее, а так-же создаём объект контекста базы данных.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/44.png)
Для получения данных из базы данных и занесения их в таблицу создадим функцию void TableRefresh. Void функции создаются в том случае, когда не нужно, чтобы функция что-то возвращала, а просто выполняла действия, которые в ней записаны.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/45.png)
В этой функции создадим var переменную, в которой будем хранить данные, которые мы будем получать из базы данных. Var переменные создаются, когда нужно создать переменную без явного указания типа. Т.к. нам нужны не все столбцы из таблицы создадим выборку.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/46.png)
В этой переменной мы используем LINQ запрос к таблице Clients. В методе расширения Select мы используем лямбда выражение, в котором создаём анонимный объект, внутри которого будут содержаться данные, которые нам нужны. В объекте сначала задаём имя переменной, а затем значение, которое будет храниться под этим именем, а также выводиться в dataGridView.
Метод расширения Count() возвращает количество записей в таблице, т.к. таблицы Client и ClientService связаны возвращается количество записей, в которых фигурирует ID клиента.
# Поиск
Сразу-же добавим Поиск. Для этого нужно добавить после Select(…) метод расширения Where(). В него вписываем условия для отбора данных через лямбда выражение. 
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/47.png)
Метод расширения Contains, который используется при отборе данных, проверяет, содержит ли запись из таблицы текст, написанный в поле на форме.
Нужно создать обработчик ввода текста пользователем. Для этого прокликиваем данные поля на форме.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/48.png)
После чего в обработчиках вызываем нашу функцию. 
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/49.png)
А так-же создадим обработчик нажатия кнопки Clear, чтобы очищать поля поиска.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/50.png)
Метод расширения Clear() очищает текст в указанном поле.

В обработчике загрузки формы тоже нужно вызвать данную функцию.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/51.png)
Это нужно, чтобы при каждом изменении полей поиска данные в dataGridView обновлялись.
Допишем в нашей функции следующую строку - 
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/52.png)
В ней мы задаём источник данных, т.е. массив, который мы получили из базы данных. Данный массив нужно привести к типу List, это делается при помощи метода расширения ToList().
При запуске приложения мы увидим, что данные загрузились из БД, и если начать вводить текст в поля сверху, то сразу-же применятся параметры поиска, и данные в таблице обновятся.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/53.png)
# Постраничный вывод данных
В ТЗ есть требование вывода постраничного вывода данных, с возможностью выбора пользователем количества строк, которые будут выводиться на странице (по 10, 50, 200, все).
Мы уже добавили массив со списком выбора количества строк. Нужно создать глобальную переменную, в которой мы будем хранить количество строк, которые нужно вывести на страницу, и количество строк, которые уже выведены. Для этого создаём данные переменные в начале класса формы.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/54.png)
А так-же заранее создадим функцию для подсчёта количества клиентов в таблице.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/55.png)
Нужно создать обработчик изменения selectBox-a с количеством строк, а так-же нажатия на кнопки Back и Next.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/56.png)
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/57.png)
В них мы прописываем логику подсчёта страниц. При вызове оператора return, void функция завершается, и не выполняет код, который написан после.
# Сортировка
Ранее мы уже добавили источник данных для поля сортировки.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/58.png)
Добавим обработчик изменения индекса выбранного значения в этом поле. В котором просто вызовем нашу основную функцию TableRefresh()
<br/>
В самой функции вместо задания источника данных из переменной создадим конструкцию switch case. Данная конструкция работает аналогично if else, но пишется проще и быстрее. Кейс default вызывается, если значение не соответствует ни одному заданному кейсу.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/59.png)
В этих запросах мы делаем сортировку данных в переменной var при помощи метода расширения OrderBy(), когда нам нужно сделать сортировку с начала, и OrderByDescending(), когда нам нужно сделать сортировку с конца. В параметрах, которые мы передаём данным методам мы используем лямбда выражения, в которых мы задаём по какому полю будет выполняться сортировка.
При помощи оператора расширения Skip() мы пропускаем определённое количество объектов в массиве данных (нашей переменной). И при помощи оператора расширения Take(), мы берём определённое количество объектов, которое мы задали в параметрах метода. После чего мы приводим это значение к типу List при помощи метода расширения ToList().
И в самом конце добавим строку изменения текста, которая будет показывать сколько строк уже было показано. 

![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/60.png)
Данная строка содержит тернарное выражение, которое работает по принципу if else. В начале пишется логическое выражение «число == другое число», после чего ставится знак вопроса. После знака вопроса пишется значение, которое возвращается если условие возвращает true. После этого значения ставится двоеточие, и пишется значение, которое возвращается если условие возвращает false.

В ТЗ есть требование, где нужно добавить возможность получения списка людей, у которых день рождения в текущем месяце.
Реализуем это через checkbox, который мы ранее создавали на форме.
Добавим обработчик изменения CheckBox-а на форме, и вложим в него вызов функции обновления таблицы.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/61.png)
В самой функции добавим условие, которое будет отбирать из массива данных объекты, в которых у поля Birthday месяц будет соответствовать текущему.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/62.png)

# Добавление и редактирование данных в таблице
Нужно создать следующую форму
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/63.png)
Поле «Телефон» реализовано через MaskedTextBox
Чтобы задать маску у данного поля нужно сначала нажать на само поле, а после на кнопку с треугольником, который появится справа сверху на нём
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/64.png)
Сама маска выглядит следующим образом
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/65.png)
Далее перейдём к коду.
Добавим контекст базы данных, и сделаем наследование от TemplateForm. Так-же на будущее определим глобальную переменную id.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/66.png)
Чтобы не делать две разные формы, мы просто создадим перегрузку метода вызова нашего класса, создав новый метод с тем-же названием и добавив ему обязательный параметр.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/67.png)
Если мы вызовем данную форму без параметра clientID, то вызовется форма добавления клиента, если с ним, то форма редактирования клиента.
Далее создадим обработчик загрузки формы(2 раза лкм по фону формы), и впишем в него следующий код (как работать с фото будет позже, просто добавим строку с определением пути)
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/68.png)
MaxLength для полей TextBox указывается для ограничения количества вводимых символов, согласно ТЗ.
Чтобы в коде различать создание от редактирования ранее была создана перемена id, и если вызывать форму, передавая id, то этот id запишется в переменную.
В форме загрузки есть условие, в котором в зависимости от наличия данной переменной мы или находим пользователя в таблице Clients при помощи метода расширения Find(), и заполняем поля на форме, или просто скрываем поля и группу элементов, которые не должны отображаться при создании пользователя.



Далее добавим обработчик кнопки сохранения данных
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/69.png)
Конструкция String.IsNullOrWhiteSpace(string), как можно понять из названия проверяет является ли значение текстового значения пустым или пробелом.
Ниже мы создаём объект var, и в нём используем тернарный оператор, в котором проверяем есть ли пользователь в таблице. Если есть, то возвращаем этого пользователя, если нету, то создаём новый объект Client().
После этого мы заполняем данные о клиенте из полей с формы.
После заполнения данных снова идёт проверка на id. Если он равняется 0, то созданный объект добавляется в таблицу Clients, после чего идёт сохранение изменений в базе данных и закрытие формы.
Если id не равняется 0, то изменённый объект просто сохраняется в таблице, и форма закрывается.

# Вызов формы
Т.к. ранее мы создали два метода вызова одной формы, нам нужно всего лишь добавить два обработчика нажатия на кнопку, которые будут вызывать эту форму.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/70.png)
В обработчике кнопки вызова формы создания пользователя мы создаём объект формы, не передавая никакие параметры. После создания объекта мы прячем основную форму, и показываем новую форму как диалог. Далее нужно добавить строку, где показывается форма, и вызвать функцию обновления таблицы. Код после вызова диалога выполнится только после его завершения.
В обработчике кнопки редактирования мы используем конструкцию try catch, чтобы если пользователь не выбрал ни одно поле показывалась ошибка. В конструкции try мы создаём переменную int, в которую записываем значение из первой клетки выбранной строки. Конвертация в Int32 нужна, т.к. данные в dataGridView хранятся как string переменные.
После мы создаём объект формы, в который передаём id, который мы получили из выбранной строки. Код дальше аналогичен тому, что был в обработчике кнопки создания.

# Работа с фотографиями
Чтобы на форме выводилась фотография нужно выполнить следующие действия –
Для начала нужно добавить папку с фотографиями «ClientImages» в папку debug, нашего проекта.
Эта папка расположена в папке bin, в корне нашего проекта.
Ранее в обработчике загрузки форомы была добавлена строчка 
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/71.png)
Она нужна для указания пути файла в ImageBox-е. Объект Environment, и его метод расширения CurrentDirectory нужен для указания текущей директории, т.е. папки debug в проекте при отладке, или в папке, где будет лежать программа в уже собранном проекте.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/72.png)
Этого достаточно, чтобы просто указать путь к фотографии, чтобы она вывелась на форме.
Загрузка фотографий
Но так-же нужно реализовать функционал загрузки фотографий для пользователя.
Для этого нужно создать обработчик нажатия на кнопку загрузки фотографии.
В нём нужно создать диалог открытия файла. Делается это при помощи создания объекта OpenFileDialog.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/73.png)
Зададим этому объекту параметр RestoreDirectory true, чтобы он сохранял путь, который был задан до закрытия нового диалога.
Ниже вызовем этот объект как диалог, и создадим условие, в котором будет проверка, успешно ли завершился диалог.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/74.png)
В самом условии создадим конструкцию try catch, чтобы не обрабатывать все возможные исключения, которые могут возникнуть.
Конструкция try выполняется как обычный код, а catch вызывается, только когда внутри try возникает ошибка.
В самой конструкции создадим string переменную, в которой будем хранить директорию, куда мы будем записывать файл.
Используя BinaryWriter мы создадим файл из байтовых значений исходной фотографии. В параметрах вызова нужно вызвать объект File, у которого нужно указать метод расширения Open, и уже в его параметрах вызова нужно сначала указать путь, где будет лежать файл, и указать что файл нужно создать при помощи FileMode.Create.
Внутри BinaryWriter-а нужно создать массив байтов, в который нужно считать все байты фотографии исходного изображения при помощи объекта File, и его метода расширения ReadAllBytes(), в параметры которого нужно передать путь открытого файла из диалога.
Далее мы запишем эти байты в файл, который был создан при вызове BinaryWriter-а. Делается это при помощи вызова нашего созданного объекта, и его метода расширения Write(), в который параметром нужно передать массив данных, который мы считали из фотографии.
После этого в PictureBox нужно задать путь к созданному файлу.

В обработчике кнопки сохранения у нас есть следующая строка
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/75.png)
В ней задаётся путь, который будет записан в базу данных. Внутри переменной мы получаем путь при помощи метода расширения ImageLocation, который был применён к PictureBox-у. После получения пути мы вызываем метод расширения Split(), для того, чтобы разделить данный путь на части, в котором указываем символ «\». Используется 2 таких символа т.к. это специальный символ, использующийся для экранирования, и если не ставить второй символ, то среда будет думать, что мы хотим задать в string переменную ковычку, и весь код за ней. После этого используется метод расширения Last(), чтобы получить последний объект из коллекции, которая была создана при вызове Split().
# Работа с тегами
На макете формы ранее был создан GroupBox, содержащий label-ы и кнопки
Зададим им значения в обработчике загрузки формы, запросив данные из таблицы Tags
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/76.png)
Далее создадим функцию проверки, есть ли у пользователя заданный тег.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/77.png)
В нём создадим запрос SqlQuery в базу данных, в котором получим количество записей содержащих id тега и id клиента. Если число больше 0, то функция возвращает true.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/78.png)
В обработчике загрузки формы нужно дописать проверки на наличие у пользователя определённых тегов.

Также нужно добавить функции добавления и удаления тега у пользователя.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/79.png)
При запросе к таблице клиентов в данном коде используется метод расширения Include, чтобы добавить взаимодействие с таблицей тегов.
Ниже есть проверка на то, есть ли пользователь в таблице. В этом условии мы через метод расширения Add добавляем переданный тег.
В коде удаления тоже самое, только с методом расширения Remove.
После чего создадим обработчики кнопок на форме.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/80.png)
После этого на форме будут показываться теги с их заданными цветами.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/81.png)

# Вывод сервисов пользователя
Создадим форму с объектом DataGridView.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/82.png)
Код данной формы выглядит следующим образом.
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/83.png)
Вызываем эту форму при помощи такого кода
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/84.png)
# Удаление пользователя
Создадим на форме кнопку, на которую повесим обработчик нажатия. В этом обработчике нужно прописать следующий код
![Image alt](https://github.com/M4ddCat/WinForms-Guide/blob/main/images/85.png)
В этом коде есть проверка, есть ли записи в таблице ClientServices содержащие id пользователя. Это нужно т.к. есть условие не удалять записи пользователей, у которых есть купленные услуги.
