# BackwardContourTracing
## Find contor by Backward contour tracing algorithms

В ході роботи над алгоритмом було розроблено програму яка шукає контур об'єкта зображення, тільки пре деяких умовах.

### Дані, на яких проводились експерименти

Для коректної роботи алгоритму потрбно подавати на вхід зображення на якому було виконанно пре-процес сегментацію,
і на зображенні не повинно бути більше 1-го об'єкта, інакше буде знайдений контур тільки 1 обєкта.

На вході алгоритм приймає:

- Матрицю пікселей зображення
- Висоту зображення
- Ширину зображення

На виході ми отримаємо список з пікселей які є контуром об'єкта зображення.

## Опис експерименту
Для експеременту було вибранно переше зображення, яке вивелось після такого запиту в Google "something on black background".
Для того щоб забезпечити себе правельнм результатом зробимо неважку сегментацію.

**Приклад виклику функції сегментації:**
```
def segmentation(width, height, pixels):
  def is_black(rgb):
    return math.sqrt(rgb[0] ** 2 + rgb[1] ** 2 + rgb[2] ** 2) < 50

  for i in range(width):
    for j in range(height):

  if not is_black(pix[i, j]):
    pix[i, j] = (255, 255, 255)

  else:
    pix[i, j] = (0, 0, 0)
```

Початкове зображення:


![Original image](http://i.prntscr.com/br01-fqnQTSISgCpDblw4A.png)

Результат пре-процесу:


![Segmentation](http://i.prntscr.com/5iS7xjKrSCqKO4Xc5Lnjrw.png)

Далі на вже обробленому зображенні шукається стартовий піксель, який є часиною контуру. Навколо нього будується восьми сітка

![Tent](http://i.prntscr.com/ZsOAfVxoT3iWI4jBCm_vRQ.png)

і вже у сітці шукається наступний активний пвксель.

Результатом роботи алгоритму буде список координаті пікселів які належать до контуру. На оригінальному зображені пікселі за знайденими результатами прирівнюються до (0,255,0) за RGB і зображення зберігається.

![Results](http://i.prntscr.com/YoGMzaeTSnSMrrnCAXP62A.png)


## Висновки

### Чому навчились при розв’язанні цієї задачі?
При роботі над цим алгоритмом  перш щ все я навчився користуватись новими бібліотеками, як працює сама обробка зображень, це дало змогу зрозуміти принцип роботи фотошопів. 

### Що викликало найбільшу складність?
Усвідомити як працює сам алгоритм і перевести його з доволі таки поганого псевдокоду в робочу програму, також в процесі довелося створювати чимало додаткових модулів і методів.

### Що лишилося незрозумілим?
Якби я не намагався але коректно запустити процес сегментації зображень я все-таки не зміг. Я перепробув значну кількість різних бібліотек і намагався писати все з 0 але так нічого і не вийшло. Хотів би попрацювати з сегментацією трішки більше.

