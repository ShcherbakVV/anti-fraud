При подключении новых проектов обычно требуется рассчитать метрики, чтобы корректно настроить
систему фрод-мониторинга исходя из данных.

Имеющиеся таблицы:

● Payments 

○ id - Уникальный номер платежа 

○ payment_date - Дата совершения платежа 

○ nick - Идентификатор пользователя 

○ payment_account - Идентификатор платежного аккаунта 

○ project_id - ID проекта в системе 

○ status - статус платежа в системе: 
  1 - транзакция в процессе обработки, 
  2 - транзакция отменена,
  3 - транзакция успешна 
  
○ amount - Сумма текущей транзакции в у.е. 

○ payment_system - Используемый платежный метод 

○ test_transaction - Флаг, является ли транзакция тестовой или нет: 1 - тест, 0 - бой

● Card_payments 

○ payment_id - ID из таблицы Payments 

○ card_brand - Тип карты 

○ card_bank - Банк, выпустивший карту 

● Games 

○ game_id - Соответствует project из таблицы payments 

○ game_name - Полное название игры

---
Необходимо составить SQL-запрос, чтобы получить таблицу с
полями:

● project - ID проекта и его название в одном поле через точку и пробел. Например: “15029. OVERWATCH”.

● successful_transactions - Число успешных платежей.

● successful_transactions_amount - Сумма успешных транзакций в у.е.

● average_check - Средний чек в проекте в у.е. (не медиана, а просто AVG от всех успешных платежей)

● max_amount_for_1_user - Максимальная сумма платежей для одного пользователя в заданном периоде в
у.е.

● TOP3_most_popular_ps - 3 самые популярные платежные системы в проекте по числу успешных платежей.

● TOP3_banks - 3 самых популярных банка по числу успешных платежей в проекте
