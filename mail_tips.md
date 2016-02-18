
<font> не используем  - юзаем span. В атрибуте style мы указываем такие параметры, как: font-family, font-size и color — обязательно в формате #xxxxxx или фактическом, например red.

Каждую отдельно взятую ссылку необходимо обернуть в span, указав для него все необходимые стили, и в тоже время продублировать все те же самые стили в атрибут style самой ссылки. 
Для всех ссылок устанавливаем значение _blank атрибута target 

Для всех изображений необходимо установить ширину и высоту равной фактической. Это можно реализовать через атрибуты width и height, а так же через css в атрибуте style тега img — разницы нет. Искажения в размерах допускать не стоит, т.к. результат может оказаться плачевным для большинства почтовиков.
Хотелось бы заметить, что в том случае, если картинка является ссылкой, то для изображения нужно обнулить border через стили или атрибут border тега img, а для самой ссылки стоит установить text-decoration:none; иначе картинка может оказаться подчеркнутой. 

It turns out that the most reliable way of coding background colors is to use the HTML bgcolor attribute with a 6-digit hex code on the table and td level: 
Никаких фоновых изображений никогда и ни под каким предлогом
Никакого java-script
Напрочь забудьте об абсолютном позиционировании
Имитируйте абцазы и списки, как это описано в предыдущей статье
Устанавливайте target="_blank" для ссылок, дабы не открывать сайты в окне почтового демона.
Всегда! Запомните, всегда устанавливайте ссылку на отписку от рассылки в тело письма! Вам за это скажут спасибо нецелевые подписчики, и пожалеет спам-фильтр.
mso-line-height-rule:exactly; line-height=""
line-height задавать  ячейкам! И только в процентах!
Если у td задан атрибут height=”” без значения, mso-line-height-rule:exactly не будет работать, нужно проставлять щначение или не использовать атрибут вовсе.
Оформление текста следует производить тегами - span. Для родительской ячейки необходимо указать line-height (это принципиально для Outlook 2013 и некоторых веб-интерфейсов). Если же в ячейке присутствует текст разного размера, то каждый блок текста следует обернуть в <div> с прописанным line-height (к слову сказать - веб-интерфейс outlook.com игнорирует line-height прописанный у td). 
При оформлении текста следует все спецсимволы заменить на соответствующий код: 

2. Обязательные свойства для HTML-тегов

Для html-тегов табличной верстки существуют свойства, которые обнуляют лишние отступы, бордеры, а также избавляют нас от некоторых багов в будущем. Их нужно использовать всегда во всех html тегах письма.
<table border="0" cellpadding="0" cellspacing="0" style="margin:0; padding:0">

border=«0» — толщина рамки в пикселах;
cellpadding=«0» — отступ от рамки до содержимого ячейки;
cellspacing=«0» — расстояние между ячейками;
style=«margin:0; padding:0» — обнуляем внутренние и внешние отступы, которые добавляет некоторые почтовые клиенты:
<a href="#" style="color: #333333; font: 10px Arial, sans-serif; line-height: 30px; -webkit-text-size-adjust:none; display: block;" target="_blank"></a>
 
<span style="color: #333333; font: 10px Arial, sans-serif; line-height: 30px; -webkit-text-size-adjust:none; display: block;"></span>

color: #333333; font: 10px Arial, sans-serif — всегда используем эти свойства для всех ссылок и спанов, иначе почтовые клиенты будут добавлять к этим свойствам свои значения;
line-height: 30px — тоже используем для всех ссылок и спанов, в ином случае почтовые клиенты будут ставить свое значение. Также этим свойством мы можем делать отступы сверху и снизу между строчными и блочными элементами;
-webkit-text-size-adjust:none — обязательное свойство для всех строчных элементов, используется для фикса проблемы с размером шрифтов на устройствах iPhone iOS 6-7/iPad. По умолчанию на этих устройствах минимальный размер шрифта 13px, это свойство решает данную проблему;
display: block — делает строчный элемент блочным:
<img src="#" alt="" border="0" width="100" style="display:block;"/>

alt="" — обязательное свойство, должно всегда использоваться, можно оставлять пустым;
border=«0» — толщина рамки в пикселях (px);
width=«100» — ширина картинки, если картинка статическая и используется ее реальный размер, то можем еще задать ее высотуheight=«100». Если нам нужно сделать размер картинки меньше чем она на самом деле, контролируем ее размер с помощью свойства width=«30» и она будет пропорционально менять и высоту и ширину;
display:block; — хак для Outlook, если не ставить display:block то Outlook добавить к картинке отступы.

Свойства background="" bgcolor="" можно применять только для тега
<table>


Для отступов можно использовать пустые ячейки таблицы с прописанной высотой или шириной, но этот метод уже устарел, так как влечет за собой нагроможденность кода. Отступы можно делать с помощью CSS свойства padding. Это свойство можно использовать для всех тегов, но имейте введу, что если его применять к тегу span, то десктопный Outlook 2007/10/13 + не будет применять отступы. 

Свойство margin тоже работает но полностью не поддерживается в веб версии почтового сервера Outlook.com. 


1. Если использовать span или другой строчный тег, то телефонные номера и e-mail адреса Gmail оборачивает в ссылку и присваивает класс с синим цветом:

Для решения этой проблемы нужно электронную почту и телефон изначально оборачивать в ссылку. Также необходимо указать нужные стили для ссылок.

Для телефона:
<a href="tel:0­ 8­00 3­03 5­05" value="+380800303505" target="_blank" style="">0­ 8­00 3­03 5­05</a>

Для электронной почты:
<a href="mailto:exemple@gmail.com" target="_blank" style="">exemple@gmail.com</a>

2. Для того, чтобы фон вне письма был на всю ширину и высоту, необходимо главной таблице добавить width=«100%» и для tdпрописать height=«100%». Пример:
<table bgcolor="#000000" border="0" cellpadding="0" cellspacing="0" style="margin:0; padding:0" width="100%">
  <tr>
    <td height="100%">


Не нужно задавать таблице height=«100%», возникают проблемы с выравниванием ячеек по вертикали внутри главной таблицы. 

Проблема заключается в том, что все ссылки при наведении становятся красными. Наверное — фирменный стиль Яндекса. Стили в head не решают проблему. Костыля не нашел, но буду признателен тому, кто поделится решением.

<a target="_blank" style="color:#ffffff !important;" href="#"><span style="color:#ffffff !important;">Текст</span></a>



<table width="746" cellpadding="0" cellspacing="0" align="center" bgcolor="#ffffff" border = "0" style=" -webkit-text-size-adjust: none; border-collapse: collapse !important; mso-table-lspace: 0pt !important; mso-table-rspace: 0pt !important; border: 0px; border-collapse:collapse; min-width:747px;"></table>

картинкам задавать ALTы, их можно стилизовать (но не везде работает) Во многих почтовых клиентах альтернативный текст исчезает, ​​как только размер или длина текста превышает ширину и/или высоту изображения. Поэтому, лучше придерживаться коротких описаний и меньшего размера шрифта, чтобы ALT текст не пропал. 

Чтобы телефоны не окрашивались
<a href="tel:(044)290-85-00" style="pointer-events: none;text-decoration:none;color:#333333;">(044) 290-85-00</a>


ресайз текста  и картинок на гмейле 
CAUSE: This problem occurs if you have an image w/in the email. When the image auto-scale, the entire email/page will auto-fit in the window.
SOLUTION: Add inline style for the image for min-width (300px so it doesn't take the entire 320px iphone width), max-width (your desired max with), and width of 100%.
i.e. image src="image.jpg" style="width: 100%; min-width: 300px; max-width: 500px;"
или
Just add min-width to your background/container table!




Words sometimes wrap awkwardly in iOS.
If your text is in a container with a width set to less than that of your text, it might wrap poorly on this device.To fix this add word-wrap:normal to your containing element:
<td style=“word-wrap:normal”>text</td> 

Stop iOS from converting your phone numbers to hyperlinks.
By default, Safari on iOS detects any text string that is formatted like a phone number and converts it to a link which allows users to call the number by simply touching it.
To remove this type of auto formatting simply add the following meta-tag:
<meta name=“format-detection” content=“telephone=no”> 

TEST 5: WRAPPING OFFENDING LINKS IN STYLED SPANS
Our final—and favorite—solution remains the same from our original post. This solution involves setting your desired link styles in classes in the <head> of your email, and adding your new class to span tags surrounding your target text.
While inline CSS is the rule of thumb for HTML email (Gmail strips out CSS in the <head> of emails), the native mail client in iOS supports embedded style sheets. Since our test email required two different link colors, we added one class for regular black text and a second for the high-contrast text at the bottom.
.appleLinksWhite a {color: #ffffff !important; text-decoration: underline;} 
.appleLinksBlack a {color: #000000 !important; text-decoration: none;}
After specifying these classes in the <head> of our email, we wrapped the offending blue text in <span> tags with the appropriate class throughout the email:
<span class=”appleLinksBlack”>866-787-7030</span>
The formerly blue and underlined text now blends with the rest of my design, and my high-contrast text has regained readability. It’s important to note, however, that each of the formerly blue links are still active. They simply blend into the surrounding text a bit better than before. Tapping these links will still trigger their associated app-based events.



Targeting Outlook
With the plethora of rendering issues that comes with having to support Outlook, it is sometimes useful to target Outlook with specific styles. Fortunately, targeting various versions of Outlook is relatively easy using conditional CSS.
<!--[if gt mso 11]>
    <style type="text/css">
        ... Specific Outlook Styles...
    </style>
<![endif]-->
Looking at the example above, you can see a conditional statement containing a style block for CSS to be used for Outlook. That conditional statement can be used to target Outlook in a variety of ways:
lt is less than a specific version.
gt is greater than a specific version.
lte is less than or equal to a specific version.
gte is greater than or equal to a specific version.
It's important to understand which versions you are targeting, too. Microsoft's numbering scheme is below:
Outlook 2000 = 9
Outlook 2002 = 10
Outlook 2003 = 11
Outlook 2007 = 12
Outlook 2010 = 14
Outlook 2013 = 15
In addition to using conditional CSS, Outlook has a variety of Microsoft-specific properties which you can use to your advantage if you're running into any particularly nasty bugs. Not many designers will utilize any of these properties, but for the purposes of documentation, here they are:


Часто необходимо, чтобы, например, предлог не был оторван от слова, чтобы это гарантировать используйте символ неразрывного пробела:

Только в&nbsp;этом году!
А если необходимо перенести слово, воспользуйтесь символом &shy; Это бывает 

Про ссылки сказать вот еще что: некоторые веб-интерфейсы и почтовые клиенты (особенно мобильные), если находят нечто похожее на номер телефона, заменяют его ссылкой, при этом используются цвета по-умолчанию. Чтобы этого избежать есть 2 вариант: либо сделать так, чтобы номер не распознавался как номер телефона, либо сразу сделать его ссылкой. В первом случае, необходимо разделить отдельные части, используя <span>
+7<span>987<span><span>654<span><span>32<span><span>10<span>
Во втором случае, Необходимо прописать ссылку вида: href="tel:+79876543210"
Аналогично первому варианту можно избежать замены адресов в веб-интерфейсе yandex.


Избегайте использования в качестве отображаемого текста ссылок url. Дело в том, что если включено отслеживание кликов, то ссылки преобразуются (например, ссылка виде http://yandex.ru станет иметь вид: http://click.domen.ru/list1/sfsdfkjkjnas90lkmmqadsplzxcwumfidqlwsdafokqvzz ). Тоесть получается что вы выводите одну ссылку, а ссылаетесь на другую - это может быть воспринято за фишинг, а письмо может быть признано мошенническим (и следовательно попадет в спам или вообще не дойдет до получаетля) 

Outlook 2013 имеет еще одну интересную особенность - при создании ячейки(<td>) меньше 19 пикселей в высоту он растянется до 19 пикселей. Во избежание этого, вы можете добавить параметр line-height при описании стиля ячейки. 
Так же как и с текстом, стоит помнить про особенность outlook 2013 – если высота изображения не превышает 19px, то у родительской ячейки необходимо указать стилевой параметр line-height. 

 <td height="40" style="-webkit-text-size-adjust: none; margin: 0; padding: 0;">
   <img src="http://services.google.com/fh/files/emails/spacer.gif" height="40" alt=""
   style="-webkit-text-size-adjust: none; display: block; margin: 0; padding: 0; border: 0;"/>
</td>




кнопка
<td align="center" valign="middle" bgcolor="#ffffff" class="btn" style="-webkit-text-size-adjust: none; text-transform: uppercase; font-family: Open Sans, Helvetica, Arial, sans-serif; font-weight: bold; font-size: 12px; color: #42a0fc; -webkit-border-radius: 15px; -moz-border-radius: 15px; border-radius: 15px; margin: 0; padding: 5px 30px;">
  <a href="" target="_blank" style="-webkit-text-size-adjust: none; text-decoration: none; color: #42a0fc; width: 600; height: 600;"><span style="-webkit-text-size-adjust: none; font-weight: 900; display: block; ">Sign In</span>
  </a>
   </td>

Кнопка:
<table border="0" cellspacing="0" cellpadding="0" width="80%"> <tr> <td bgcolor="#0b534a" style="padding: 12px 18px 12px 18px; -webkit-border-radius:3px; border-radius:3px" align="center"><a href="https://litmus.com" target="_blank" style="font-size: 16px; font-family: Helvetica, Arial, sans-serif; font-weight: normal; color: #ffffff; text-decoration: none;">Visit Litmus</a></td> </tr> </table> 





 <img src="http://services.google.com/fh/files/emails/header_02.png" width="100%"
                            height="auto" alt="New Features" style="display: block; margin: 0px; padding: 0; border: 0;"
                            />

http://esputnik.com/blog/kak-podruzhitsya-email-rassylke-s-mobilnym-telefonom
http://habrahabr.ru/post/227229/



<!--[if gte mso 9]><![endif]-->  target clients that have outlook 2007 or higher. 






Текст не форматировать (нет переносам), он должен быть одним блоком, чтобы мог тянуться в зависимости от отображения шрифта.
Не помещать текст в контйенер с ограниченной высотой, либо рисовать контейнер так, чтобы он мог легко тянуться(объяснить на примере боковых и верх/низ плашек)
не использовать шрифт менее 14pt 
ширина макета - 600-650 Px
Графические элементы не должны выходить за тело письма
 не используйте для текста эффектов типа обводки и мебуквенного интервала. Просто текст.
Картинок должно быть столько, чтобы сообщение выглядело хорошо и без них, ведь картинки будут блокированы браузером у многих читателей.
Обязательно должна быть сссылка для отписки

По-возможности избегать усложнений графики, ибо любое усложнение -  это потенциальные косяки. 
Так как смотрят на маленьких экранах — элементы управления должы быть большие.

