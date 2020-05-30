# Лабораторная работа № 7. Задача Коши.
Выполнил студент группы 429  
Пластова Полина Игоревна
## Вариант № 24
Решить с помощью **симметрической неявной схемы** задачу Коши  
![](/images/1.jpg)  
![](/images/2.jpg)  
с заданной относительной точностью 0.01.
Требуется построение графиков y(x), y'(x), а так же фазовых траекторий.
## Теоретическая часть
Задачу необходимо представить в виде:
![](/images/3.jpg)  
Здесь А(х) - квадратная матрица размера s×s с  элементами, зависящими от x, u(x), phi(x) - вектор-функции размерности s.  
Под двуслойной схемой понимают разностное уравнение, связывающее значение вектора y(x) для двух слоев значений аргументов ![](/images/4.jpg) и ![](/images/5.jpg). В канонической форме это соотношение задают в виде:  
![](/images/6.jpg),  
где B,A - квадратные матрицы порядка s×s, ![](/images/7.jpg) - векторы размерности s. Если B=E, то каноническую схему называют*явной*, в противном случае - *неявной*.  

*Симметрическая схема* ![](/images/8.jpg)  
![](/images/9.jpg)

Для нахождения значения также используется схема "предиктор-корректор". То есть сначала делается "предсказание" с помощью явного метода Эйлера  
![](/images/10.jpg),  
а затем проводится коррекция с помощью симметрической схемы.  
Для выбора шага, соответствующего заданной погрешности, используется правило Рунге:  
![](/images/11.jpg).
## Практическая часть  
В программе используются следующие функции:
- void Euler(double h) - делает "предсказание" методом Эйлера, принимает величину шага.
- void simmetr(double h) - реализует симметрическую схему, принимает величину шага.
- void make_values(double h, ofstream& fout) - прогоняет х от 0 до 2, получает с помощью предыдущих функций и пишет в файл значения x, y(x), y'(x).  
- void make_sum(ofstream& fout,ifstream& fin) - вспомогательная функция подсчета сумм для правила Рунге.
- void Runge(ofstream& fout,ifstream& fin) - реализация правила Рунге, подбирает шаг, нужный для расчетов с заданной погрешностью.
В int main() после подбора шага вычисляется c помощью make_values финальный вариант файла с x, y(x), y'(x). 

**Порядок компиляции/запуска:**
1. osn.cpp
2. l7.py

**Дополнительные задания:**
1. calc.py - сопоставляются приближенное решение, полученное в основновном задании, и точное решение, найденное с помощью онлайн-калькулятора.
2. vstr.py - сопоставляются приближенное решение, полученное в основновном задании, и решение, найденное с помощью встроенной функции.
### Результаты

В результате работы программы было найдено решение задачи Коши  
![](/images/1.jpg)  
![](/images/2.jpg)  
и построены графики y(x), y'(x), фазовая траектория - y'(y). Была использована симметрическая неявная схема в связке с методом Эйлера, который позволил делать "предсказания" для схемы предиктор-корректор. Необходимый шаг был найден за 5 итераций от начального h=0.8 и оказался равен 0.025.
- Результат работы основной программы (приближенное решение): 
![](/images/12.jpg)  
- Приближенное решение и точное решение, найденное с помощью онлайн-калькулятора:  
![](/images/17.jpg)  
![](/images/18.jpg)
![](/images/13.jpg)  
Разностные функции:  
![](/images/14.jpg)
- Приближенное решение и точное решение, найденное с помощью встроенной функции scipy.integrate.odeint:  
![](/images/15.jpg)  
Разностные функции:  
![](/images/16.jpg)