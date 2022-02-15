Сниппет для вывода данных, разделённых через определённые разделители. Удобно использовать для вывода значений полей документов, сформированных виджетом [mm_ddMultipleFields](https://docs.evo.im/04_extras/managermanager/03_vidzhety.html#collapse322)

# Возможности

- Получение необходимого поля документа (и TV) по id. Параметры «inputString_docField» и «inputString_docId».
- Вывод необходимого количества значений по номерам строк и и значениям. Параметры «startRow», «totalRows» и «filter».
- Вывод необходимых значений по номерам колонок. Параметр «columns».
- Сортировка строк по значениям колонок перед выводом ('ASC', 'DESC', 'RAND', 'REVERSE'), в том числе множественная сортировка. Параметры «sortDir» и «sortBy».
- Вывод значений через разделители строк и колонок. Параметры «rowGlue» и «colGlue».
- Удаление пустых значений колонок и строк перед выводом. Параметры «removeEmptyRows» и «removeEmptyCols».
- Типографирование значений перед выводом (используется сниппет (ddTypograph)[https://docs.evo.im/04_extras/ddtypograph.html]). Параметр «typography».
- URL-кодирование результата перед выводом. Параметр «urlencode».
- Вывод результата в JSON. Параметр «outputFormat».
- Вывод значений по шаблонам (чанкам) строк и колонок (в шаблоне строк также доступен плэйсхолдер <span>[</span>+rowNumber+] с номером строки). Параметры «rowTpl» и «colTpl».
- Вывод результата выполнения в чанк «outerTpl» с передачей дополнительных данных через параметр «placeholders».

# Документация

Необходимо передавать один из «inputString» / «inputString_docField» параметров.

**Описание параметров**

<table class="table table-bordered table-vcenter flip-content">
	<thead class="flip-content bordered-palegreen">
		<tr>
			<th>Название</th>
			<th>Описание</th>
			<th>Допустимые значения</th>
			<th>Значение по умолчанию</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td class="em">inputString<span class="help" title="Обязательный параметр">*</span></td>
			<td colspan="1">Исходная строка, содержащая значение с разделителями.</td>
			<td>{separated string}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>inputString_docField</td>
			<td colspan="1">Имя поля документа / TV, содержащего значение. В этом случае параметр «inputString» игнорируется, значение получается из поля документа.</td>
			<td>{string}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>inputString_docId</td>
			<td colspan="1">ID документа, значение поля которого нужно получить. Если id не задан, берётся id текущего документа.</td>
			<td>{integer}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>rowDelimiter</td>
			<td colspan="1">Разделитель между строками в исходной строке.</td>
			<td>{string; regexp}</td>
			<td>'||'</td>
		</tr>
		<tr>
			<td>colDelimiter</td>
			<td colspan="1">Разделитель между колонками в исходной строке.</td>
			<td>{string; regexp}</td>
			<td>'::'</td>
		</tr>
		<tr>
			<td>startRow</td>
			<td colspan="1">Номер строки, начиная с которой необходимо возвращать (строки нумеруются с 0).</td>
			<td>{integer}</td>
			<td>0</td>
		</tr>
		<tr>
			<td>totalRows</td>
			<td colspan="1">Количество возвращаемых строк. При значении == 'all' будут возвращены все имеющиеся строки.</td>
			<td>{integer; 'all'}</td>
			<td>'all'</td>
		</tr>
		<tr>
			<td>columns</td>
			<td colspan="1">Номера колонк через запятую, которые нужно вернуть (колонки нумеруются с 0). При значении == 'all' будут возвращены все колонки.</td>
			<td>{comma separated string; 'all'}</td>
			<td>'all'</td>
		</tr>
		<tr>
			<td>filter</td>
			<td colspan="1">Фильтр по значениям колонок. Например, при '0::a||0::b||1::1' выведутся только строки, в которых значение колонки 0 равно 'a' или 'b' и значение колонки 1 равно '1'.</td>
			<td>{separated string}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>removeEmptyRows</td>
			<td colspan="1">Удалять пустые строки?</td>
			<td>{0; 1}</td>
			<td>1</td>
		</tr>
		<tr>
			<td>removeEmptyCols</td>
			<td colspan="1">Удалять пустые колонки?</td>
			<td>{0; 1}</td>
			<td>1</td>
		</tr>
		<tr>
			<td>sortBy</td>
			<td colspan="1">Номер колонки (нумеруются с ноля), по которой необходимо сортировать. Для множественной сортировки параметры указываются через запятую (например: '0,1').</td>
			<td>{comma separated string}</td>
			<td>0</td>
		</tr>
		<tr>
			<td>sortDir</td>
			<td colspan="1">Направление сортировки строк. При значении == 'REVERSE' строки будут возвращены в обратном порядке.</td>
			<td>{'ASC'; 'DESC'; 'RAND'; 'REVERSE'; ''}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>typography</td>
			<td colspan="1">Номера колонок через запятую, значения которых нужно типографировать (колонки нумеруются с 0). Если не задано, ничего не типографируется.</td>
			<td>{comma separated string}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>outputFormat</td>
			<td colspan="1">Формат, в котором возвращать результат.</td>
			<td>{'html'; 'JSON'; 'array'; 'htmlarray'}</td>
			<td>'html'</td>
		</tr>
		<tr>
			<td>rowGlue</td>
			<td colspan="1">Разделитель (объединитель) между строками при выводе. Может использоваться совместно с шаблоном «rowTpl».</td>
			<td>{string}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>colGlue</td>
			<td colspan="1">Разделитель (объединитель) между колонками при выводе. Может использоваться совместно с шаблоном «colTpl» (но не «rowTpl», по понятным причинам).</td>
			<td>{string}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>rowTpl</td>
			<td colspan="1">Шаблон для вывода строк (параметр «outputFormat» должен быть == 'html').
				<p>Доступные плэйсхолдеры:</p>
				<ul>
					<li>[+rowNumber+] – номер строки, начинающийся с 1;</li>
					<li>[+rowNumber.zeroBased+] – номер строки, начинающийся с 0;</li>
					<li>[+total+] – общее количество строк;</li>
					<li>[+resultTotal+] – количество возвращаемых строк;</li>
					<li>[+col0+], [+col1+], … – значения соответствующих колонок.</li>
				</ul>
				<p>Передавать код напрямую без чанка можно начиная значение с «@CODE:».</p></td>
			<td>{string: chunkName|string}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>colTpl</td>
			<td colspan="1">Список шаблонов для вывода колонок, через запятую (параметр «outputFormat» должен быть == 'html'). Если шаблонов меньше, чем колонок, для всех недостающих выставляется последний указанный шаблон. Значение 'null' – без шаблона.
				<p>Доступные плэйсхолдеры:</p>
				<ul>
					<li>[+val+] – значение;</li>
					<li>[+rowNumber+] – номер строки, начинающийся с 1;</li>
					<li>[+rowNumber.zeroBased+] – номер строки, начинающийся с 0.</li>
				</ul>
				<p>Передавать код напрямую без чанка можно начиная значение с «@CODE:».</p></td>
			<td>{comma separated string: chunkName|string; 'null'}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>outerTpl</td>
			<td colspan="1">Шаблон внешней обёртки (при «outputFormat» != 'array').
				<p>Доступные плэйсхолдеры:</p>
				<ul>
					<li>[+result+] – результат сниппета;</li>
					<li>[+total+] – общее количество строк;</li>
					<li>[+resultTotal+] – количество возвращаемых строк;</li>
					<li>[+rowY.colX+] – значение (где «Y» – номер строки, «X» – номер колонки).</li>
				</ul>
				<p>Передавать код напрямую без чанка можно начиная значение с «@CODE:».</p></td>
			<td>{string: chunkName|string}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>placeholders</td>
			<td colspan="1">Дополнительные данные в виде <a href="https://en.wikipedia.org/wiki/Query_string" target="_blank">query string</a> которые будут переданы в шаблоны «outerTpl», «rowTpl» and «colTpl». Например, «pladeholder1=value1&pagetitle=My awesome pagetitle!».</td>
			<td>{query string}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>urlencode</td>
			<td colspan="1">Надо URL-кодировать результирующую строку (при «outputFormat» != 'array')? Строка кодируется согласно RFC 3986.</td>
			<td>{0; 1}</td>
			<td>0</td>
		</tr>
		<tr>
			<td>totalRowsToPlaceholder</td>
			<td colspan="1">Имя внешнего плэйсхолдера, в который нужно вывести общее количество строк. Если параметр не задан – не выводится.</td>
			<td>{string}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>resultToPlaceholder</td>
			<td colspan="1">Имя внешнего плэйсхолдера, в который нужно сохранить результат работы сниппета вместо обычного вывода. Если параметр не задан – сниппет просто возвращает реузльтат.</td>
			<td>{string}</td>
			<td>–</td>
		</tr>
	</tbody>
</table>

# Примеры

**Вывод изображений с описаниями**

Исходная строка (пусть находится в TV документа «images»):

`assets/images/some_img1.jpg::Изображение 1||assets/images/some_img2.jpg::Изображение 2`


Вызов сниппета в шаблоне документа:
```php
  [[ddGetMultipleField?
    &inputString=``
    &rowTpl=`images_item`
  ]]
```

Код чанка «images_item»:
```php
[+col1+]:
<img src="[+col0+]" alt="[+col1+]" />
```

**Получение и вывод данных из поля (TV) «prices» документа №25 в виде таблицы**

Исходное значение поля:
<pre class="brush: html;">Яблоки вкусные::100::кг||Гвозди обыкновенные::5 000::центнер||Коты::865::шт</pre>

<p>Вызов сниппета (где угодно):</p>
<pre class="brush: html;">
[[ddGetMultipleField?
&amp;inputString_docField=`prices`
&amp;inputString_docId=`25`
&amp;outerTpl=`prices`
&amp;rowTpl=`prices_item`
]]</pre>

<p>Код чанка «prices_item»:</p>
<pre class="brush: html;">
&lt;tr&gt;
	&lt;td&gt;[+rowNumber+]&lt;/td&gt;
	&lt;td&gt;[+col0+]&lt;/td&gt;
	&lt;td&gt;[+col1+] руб./[+col2+]&lt;/td&gt;
&lt;/tr&gt;</pre>

<p>Код чанка «prices»:</p>
<pre class="brush: html;">
&lt;h1&gt;Табличка цен&lt;/h1&gt;
&lt;table&gt;
	[+result+]
&lt;/table&gt;
</pre>

<h4>Вывод тегов документа через запятую с использованием регулярного выражения в «rowDelimiter»</h4>
<p>Пусть теги документа у нас хранятся в TV «tags» и к этой TV у нас применён виджет <a href="130.html">mm_widget_tags</a>. Пользователь заполняет теги через запятую, при этом, может заполняться как с пробелами по краям, так и без них.</p>
<p>Значение TV «tags»:</p>
<pre class="brush: html;">
Коты, Кошки,Собаки , Медведи ,Слоны</pre>
<p>Вызов сниппета в шаблоне документа:</p>
<pre class="brush: html;">
[[ddGetMultipleField?
&inputString=`Manager, General`
&rowDelimiter=`/\s*,\s*/`
&rowGlue=`, `
&rowTpl=`tags_row`
]]
</pre>
<p>Код чанка «tags_row»:</p>
<pre class="brush: html;">
&lt;a href="dlbuildmenu/kratkoe-opisanie?tags=[+col0+]"&gt;[+col0+]&lt;/a&gt;</pre>

<p>Результат:</p>
<pre class="brush: html;">
&lt;a href="dlbuildmenu/kratkoe-opisanie?tags=Коты"&gt;Коты&lt;/a&gt;,
&lt;a href="dlbuildmenu/kratkoe-opisanie?tags=Кошки"&gt;Кошки&lt;/a&gt;,
&lt;a href="dlbuildmenu/kratkoe-opisanie?tags=Собаки"&gt;Собаки&lt;/a&gt;,
&lt;a href="dlbuildmenu/kratkoe-opisanie?tags=Медведи"&gt;Медведи&lt;/a&gt;,
&lt;a href="dlbuildmenu/kratkoe-opisanie?tags=Слоны"&gt;Слоны&lt;/a&gt;
</pre>

<h4>Передача дополнительных данных через параметр «placeholders»</h4>
<pre class="brush: html;">
[[ddGetMultipleField?
&inputString=`Серый::8 кг::любит мясо||Рыжий::6 кг::вегетарианец`
&outerTpl=`cats`
&rowTpl=`cats_item`
&colTpl=`cats_item_color,null,null`
&placeholders=`kind=коты`
&price=`не продаётся.`
&colorTitle=`Шерсть густая, хорошая`
]]
</pre>
<p>Код чанка «cats» (вместо «[+kind+]» подставятся «коты»):</p>
<pre class="brush: html;">&lt;h1&gt;Наши любимые [+kind+], [+resultTotal+] штук.&lt;/h1&gt;[+result+]</pre>
<p>Код чанка «cats_item» (вместо «[+price+]» подставится «не продаётся.»):</p>
<pre class="brush: html;">[+rowNumber+]. [+col0+], весит [+col1+], [+col2+] – &lt;i&gt;[+price+]&lt;/i&gt;&lt;br /&gt;</pre>
<p>Код чанка «cats_item_color» (вместо «[+colorTitle+]» подставится «Шерсть густая, хорошая»):</p>
<pre class="brush: html;">&lt;span title="[+colorTitle+]"&gt;[+val+]&lt;/span&gt;</pre>
