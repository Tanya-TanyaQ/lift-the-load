class HoistSystem:
    def __init__(self, max_weight_tons, max_height_m):
        self.max_weight = max_weight_tons * 1000  # в кг
        self.max_height = max_height_m  # в метрах
        self.current_height = 0
        self.motor_on = False

    def read_weight_sensor(self):
        # Эмуляция считывания веса (например, от датчика)
        return 10250  # кг, например

    def read_height_sensor(self):
        # Эмуляция высоты
        return self.current_height

    def start_motor(self):
        self.motor_on = True
        print("Мотор включён, подъем начат...")

    def stop_motor(self):
        self.motor_on = False
        print("Мотор остановлен.")

    def raise_cargo(self, target_height):
        if target_height > self.max_height:
            print("Ошибка: высота превышает допустимую.")
            return

        weight = self.read_weight_sensor()
        if weight > self.max_weight:
            print("Ошибка: груз слишком тяжёлый!")
            return

        self.start_motor()
        while self.current_height < target_height:
            self.current_height += 5  # поднимается на 5 м за такт
            print(f"Текущая высота: {self.current_height} м")
            if self.current_height >= target_height:
                break
        self.stop_motor()
        print(f"Груз поднят на {self.current_height} метров.")

# --- Использование:
hoist = HoistSystem(max_weight_tons=12, max_height_m=500)
hoist.raise_cargo(target_height=420)
# lift-the-load
