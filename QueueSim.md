🚶 Queue Simulator - Симулятор Очереди (код внизу)
Реалистичный симулятор очереди на Python, который позволяет почувствовать всю "радость" ожидания в очереди с случайным временем обслуживания.

🎯 О проекте
Ever wondered what it feels like to stand in a virtual queue? Now you can! Queue Simulator воссоздает аутентичный опыт ожидания в очереди с непредсказуемым временем обслуживания каждого человека.

Проект был создан для:

Демонстрации работы с временными интервалами в Python

Симуляции реальных процессов с случайными величинами

Напоминания о том, как важно ценить свое время 😄

✨ Особенности
⏱️ Реальное время ожидания - программа действительно ждет указанное время

🎲 Случайные интервалы - от 30 секунд до 2 минут на человека

📊 Динамическая статистика - отслеживание позиции и времени

🎯 Реалистичность - вы всегда начинаете с конца очереди

📊 Пример вывода

🚶 Начинается симуляция очереди!

Всего людей в очереди: 12

Вы стоите на позиции: 12

----------------------------------------

⏰ Обслуживание человека... (78.4 сек)

✅ Обслужен 1-й человек

📊 Ваша текущая позиция: 11

🕒 Прошло времени: 1 мин 18 сек

------------------------------

...
🎉 Подошла ваша очередь! Обслуживание... (45.2 сек)


🏁 ОБСЛУЖИВАНИЕ ЗАВЕРШЕНО!

📈 Всего обслужено людей: 12

⏱️ Общее время ожидания: 15 мин 32 сек

Вот код:

    import time
    import random
    class QueueSimulator:
        def __init__(self):
            self.queue_position = 0
            self.total_people = random.randint(5, 20)  
            self.my_position = self.total_people - 1  
            self.start_time = time.time()
        
    def simulate_queue(self):
        print(" Начинается симуляция очереди!")
        print(f"Всего людей в очереди: {self.total_people}")
        print(f"Вы стоите на позиции: {self.my_position + 1}")
        print("-" * 40)
        
        served_count = 0
        
        while self.my_position > 0:
            
            service_time = random.uniform(30, 120)
            
            print(f"Обслуживание человека... ({service_time:.1f} сек)")
            time.sleep(service_time)
            
            served_count += 1
            self.my_position -= 1
            
            current_time = time.time() - self.start_time
            minutes = int(current_time // 60)
            seconds = int(current_time % 60)
            
            print(f"Обслужен {served_count}-й человек")
            print(f"Ваша текущая позиция: {self.my_position + 1}")
            print(f"Прошло времени: {minutes} мин {seconds} сек")
            print("-" * 30)
        
        
        final_service_time = random.uniform(30, 120)
        print(f"Подошла ваша очередь! Обслуживание... ({final_service_time:.1f} сек)")
        time.sleep(final_service_time)
        
        total_time = time.time() - self.start_time
        total_minutes = int(total_time // 60)
        total_seconds = int(total_time % 60)
        
        print("\n" + "="*50)
        print("ОБСЛУЖИВАНИЕ ЗАВЕРШЕНО!")
        print(f"Всего обслужено людей: {served_count + 1}")
        print(f"Общее время ожидания: {total_minutes} мин {total_seconds} сек")
        print("="*50)


    if __name__ == "__main__":
        simulator = QueueSimulator()
        simulator.simulate_queue()

hf
