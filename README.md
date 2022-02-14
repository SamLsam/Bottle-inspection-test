# Bottle-inspection-test
<p><h4>Проверка возможности работы нейросети в задаче object detection при стандартных расположениях камер (полукругом) инспекционного оборудования для распознования некоторых браков при производстве бутылочной тары.</h4></p>
<p>Датасет: 2388 стандартных фотографий инспекционного оборудования различных бутылок. </p>
<p>Разметка: labelme, переведены в формат yolo (JSON_converter.ipynb). </p>
<p>5 меток классов: "bottle" - бутылка, "inclusion" - включение инородного тела, "bubble" - пузырь, "seam" - грубый шов, "filament" - стеклянная нить.</p>
<p>Train - 2054, valid - 334.</p>
<p>NN: finetune yolov5 (8 batch, img 512, yolov5m.pt, 75 epochs, freeze backbone). AP50: ~ 45</p>
<p>Предполагается обработка изображений в реальном времени на Jetson модулях или им подобных </p>
<p>Не использовались augmentation техники, в датасете присутствует сильный дизбаланс классов, качество изображений для детекции мелких пузырей недостаточно высокое. Но при всех этих недостатках итог многообещающий даже для таких вводных, поскольку фотографирование одного объекта несколькими камерами с нескольких ракурсов дает возможность применить метод голосования (soft/hard voting). Также стоит помнить, что при тех. контроле нет задачи точной локализации брака, это задаче скорее классической классификации.</p>
<p>Интересен метод фотографирования через линейную камеру сканирующим способом при центрировании бутылки на карусели с последующим применением object detection для развертки с более высоким качеством изображения.</p>
