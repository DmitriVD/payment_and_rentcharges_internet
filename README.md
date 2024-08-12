# telecommunications_operator
Internet operator. Payments and rentcharges

Цели проекта:
Анализ платежей и списаний абонентской платы абонентов физических лиц интернет-оператору, с целью анализа текущей системы тарификации,  выявления и оценки ее недостатков, уменьшения недополученной прибыли, а также разработка рекомендаций стейкхолдерам в составлении оптимальной тарифной сетки для максимизации прибыли без существенных потерь клиентской базы.

Для исследования были взяты выгрузки из биллинга по платежам (payments), списаниям (rentcharges), тарифы заведенные в биллинге (tarifs), а также для удобства работы с учетными записями таблица с учетными записями (vgroups)

Содержание:

- Анализ платежей
	- Обзор
	- Общий анализ поступавших платежей

- Анализ списаний
	- Обзор
	- Оценка количества ушедших абонентов. Оценка сезонности
	- Оценка недополученной прибыли из-за пропусков платежей

- Финальный расчет общей статистики с учетом всех корректировок

- Выводы



Описание полей:

payments:

record_id' - Идентификатор платежа

'agrm_id' - Идентификатор лицевого счета зачисления платежа

'amount' - Сумма платежа

'pay_date' - Дата приема платежа

'manager_id' - Идентификатор менеджера создавшего/изменившего платёж

'status' - Статус платежа: 0-платеж проведен, 1-проведен и подтвержден сверкой (при загрузке файла сверки), 2-платеж аннулирован

'uid' - Идентификатор пользователя

'descr' - Описание тарифа

'rent' - Величина аренды в валюте тарифа

'shape' - Ограничение полосы пропускания Кбит/с


rentcharges:

'record_id' - Идентификатор платежа

'vg_id' - Идентификатор учетной записи

'period' - День, за который выполнено списание

'dateofcharge' - Дата и время списания

'amount' - Фактическое списание в валюте договора

'tar_id' - Идентификатор тарифа

'block' - Состояние блокировки учетной записи на момент списания

'agrm_id' - Идентификатор расчетного счета, с которого списана абон. плата

'mul' - Множитель для абон. платы в случае, когда а/п списывается пропорционально присвоенным тел. номерам

'c_date' - Начало отчетного периода, в рамках которого тарифицировалась запись

'tariff_modifier_id' - Идентификатор применяемой скидки из tariff_modifiers, NULL-если скидка не пред-сь

'user_packet_id' - Идентификатор пользовательского пакета user_packets, NULL-если УЗ не в пакете

'amount_disc' - Размер предоставленной скидки в валюте договора