### Шанс вопроса: 3%

Паттерн Мост (Bridge) — это структурный шаблон проектирования, который позволяет разделить большую абстракцию и её реализацию таким образом, что они могут изменяться независимо друг от друга. Это достигается за счёт передачи объекта-реализации (bridge) через абстракцию, позволяя реализовать различные версии и расширения без изменения клиентского кода.

**Пример на Python:**

Предположим, у нас есть приложение для работы с устройствами, например, пультами дистанционного управления для телевизоров и радиоприёмников. Мы можем использовать паттерн Мост для разделения абстракции (пульта дистанционного управления) и его реализации (конкретные команды для устройств).

```python
# Абстракция
class Remote:
    def __init__(self, device):
        self.device = device

    def power(self):
        pass

    def volume_up(self):
        pass

    def volume_down(self):
        pass

# Конкретная реализация для телевизора
class TV:
    def turn_on(self):
        print("Телевизор включен")

    def turn_off(self):
        print("Телевизор выключен")

    def increase_volume(self):
        print("Увеличение громкости телевизора")

    def decrease_volume(self):
        print("Уменьшение громкости телевизора")

# Конкретная реализация для радиоприёмника
class Radio:
    def turn_on(self):
        print("Радио включено")

    def turn_off(self):
        print("Радио выключено")

    def increase_volume(self):
        print("Увеличение громкости радио")

    def decrease_volume(self):
        print("Уменьшение громкости радио")

# Конкретные классы, наследующие от Remote и Device
class TVRemote(Remote):
    def power(self):
        self.device.turn_on()

    def volume_up(self):
        self.device.increase_volume()

    def volume_down(self):
        self.device.decrease_volume()

class RadioRemote(Remote):
    def power(self):
        self.device.turn_on()

    def volume_up(self):
        self.device.increase_volume()

    def volume_down(self):
        self.device.decrease_volume()

# Использование
tv = TV()
radio = Radio()

tv_remote = TVRemote(tv)
radio_remote = RadioRemote(radio)

tv_remote.power()  # Вывод: Телевизор включен
tv_remote.volume_up()  # Вывод: Увеличение громкости телевизора

radio_remote.power()  # Вывод: Радио включено
radio_remote.volume_down()  # Вывод: Уменьшение громкости радио
```

В этом примере `Remote` является абстракцией, а `TV` и `Radio` представляют собой различные реализации этой абстракции. Паттерн Мост позволяет нам изменять или добавлять новые устройства (реализации) без изменения клиентского кода, что делает систему более гибкой и расширяемой.