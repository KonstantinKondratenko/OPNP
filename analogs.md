# Сравнение аналогов
## Принцип отбора аналогов

Поиск аналогов производился путем поиска статей на платформе google scholar, c помощью комбинации следующие ключевые слова:
UAV trajectory flight path planning building aerial 3d reconstruction quality models photogrammetric photogrammetry.
Так были использованы следующие запросы:
1. UAV trajectory planning for building reconstruction
2. UAV trajectory planning for building photogrammetry
3. path planning for aerial 3d reconstruction 
4. flight path and quality photogrammetric models

Таким образом производился поиск синонимичных конструкция. В рамках моей задачи одинаково хорошо подходят и UAV trajectory, и flight path, и path planning. Отбирались относительно новые статьи (все, кроме одной написаны не раньше 2020 года, а оставшаяся в 2018 году).

### Real-Time UAV Path Planning for Autonomous Urban Scene Reconstruction[1]
Решение строит траекторию и производит облет на основе карты местности (участка города). По карте находятся координаты тех здание, которые необходимо облететь. На основании углов зданий, как на углах, строится связанный граф. Выбор последовательности облета зданий производится с помощью алгоритма дейкстры, движение вдоль здания - с помощью решении задачи о китайском почтальоне. 

### Flight Path Setting and Data Quality Assessments for Unmanned-Aerial-Vehicle-Based Photogrammetric Bridge Deck Documentation[2]
Координаты целевого объекта (моста). В ходе проведения съемки происходит итеративный облет объекта на разной высоте (10 15 20 30 40 метров) и под разными углами (0, +-30 и +-45 градусов по отношению к нормали плоскости). В результате авторы приходят к выводу, что чем ниже летит БПЛА, тем больше данных он собирает и тем детальнее получается модель.

### A multi-UAV cooperative route planning methodology for 3D fine-resolution building model reconstruction[3]
На основе вида объекта сверху происходит выделение его контуров. Траектория состоит из трех этапов - облет объекта сверху по площади, облет по периметру сверху, облет по периметру с уменьшением высоте при облете (после полного облета периметра снижается высота и процесс повторяется). Поскле чего в статье описывается, как можно расширить эту идею на использование нескольких дронов, но в рамках задачи это не интересует нас.

### Sampling-Based Path Planning for High-Quality Aerial 3D Reconstruction of Urban Scenes[4]
Производится первичный облет объекта для построения его грубой модели. Запускается повторный облет, который анализрует результат первого облета -- для каждой точки первичного облета рассматривается набор кандидатов на улучшения точки обзора в окрестности этой точки. Кандидаты оцениваются по следующим парматерам: близость к области худшего построения первичной модели, евклидово расстояние от точки первичного облета, угол между нормалью к плоскости целвлого объекта и углом обзора. Для каждой точки первичного облета жадным образом происходит выбор оптимального кандидата по описанным выше параметрам.

### Informed Sampling Exploration Path Planner for 3D Reconstruction of Large Scenes[5]
Нет первыичных данных о целовом объекте (ни первичного облета, ни фото сверху). При сборе данных анализируются границы поверхности целевого объекта, границы представляют собой области, где известная модель резко обрывается, указывая на наличие неисследованных участков. Для каждой точки на границах поверхности алгоритм оценивает потенциальную информационную отдачу, которую можно получить, произведя съемку в этой точке. Точки ранжируются по удаленности от текущего положения и объема информационной отдачи. Переход между точками производится на базе алгоритма A*. Процесс итеративно повторяется.

## Критерии сравнения аналогов
Все представленные решения можно разделить на две категории - те, которые требует первичный облет для построения грубой модели и ее уточенения, и те, которые производят съемку в рамках одного полета, однако поскольку этот критерий бинарный, его не выносим в качестве отдельного критерия.

### Входные данные

Необходимые входные данные для построения траектории. 

### Метод построения ключевых точек траектории

На каком основании принимается решение о том, в каких точках и в каком ракурсе необходимо производить съемку. 

### Метод движения между ключевыми точками

Каким способов БПЛА перемещается между ключевыми точками

## Таблица сравнения аналогов

## Выводы по итогам сравнения

# Выбор метода решения

# Список использованных источников

1. Q. Kuang, J. Wu, J. Pan and B. Zhou, "Real-Time UAV Path Planning for Autonomous Urban Scene Reconstruction," 2020 IEEE International Conference on Robotics and Automation (ICRA), Paris, France, 2020, pp. 1156-1162, doi: 10.1109/ICRA40945.2020.9196558. URL: https://ieeexplore.ieee.org/abstract/document/9196558
2. Chen, S.; Zeng, X.; Laefer, D.F.; Truong-Hong, L.; Mangina, E. Flight Path Setting and Data Quality Assessments for Unmanned-Aerial-Vehicle-Based Photogrammetric Bridge Deck Documentation. Sensors 2023, 23, 7159. URL: https://www.mdpi.com/1424-8220/23/16/7159 
3. Xiaocui Zheng, Fei Wang, Zhanghua Li, A multi-UAV cooperative route planning methodology for 3D fine-resolution building model reconstruction, ISPRS Journal of Photogrammetry and Remote Sensing, Volume 146, 2018. URL: https://www.sciencedirect.com/science/article/abs/pii/S0924271618303009?casa_token=Mfp5ZWq9VyAAAAAA:hRvYATwzphicXxVzRqacYFtmlaTsiJph8OAEvHhvTMQsu1WZWhYGUwKqbkPazJt8627YQ09UNw
4. Yan, F.; Xia, E.; Li, Z.; Zhou, Z. Sampling-Based Path Planning for High-Quality Aerial 3D Reconstruction of Urban Scenes. Remote Sens. 2021 URL: https://www.mdpi.com/2072-4292/13/5/989
5. Y. Kompis, L. Bartolomei, R. Mascaro, L. Teixeira and M. Chli, "Informed Sampling Exploration Path Planner for 3D Reconstruction of Large Scenes," in IEEE Robotics and Automation Letters, vol. 6, no. 4, pp. 7893-7900, Oct. 2021. URL: https://ieeexplore.ieee.org/document/9507252
6. Открытый код для статьи Informed Sampling Exploration Path Planner for 3D Reconstruction of Large Scenes  URL:  https://github.com/ethz-asl/mav_active_3d_planning
