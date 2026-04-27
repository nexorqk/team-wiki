# Design

## Design Handoff

1. Дизайнер создаёт финальные макеты в Figma
2. Дизайнер добавляет метку **ready for dev** в Figma
3. Дизайнер проводит walkthrough с назначенным разработчиком
4. Разработчик создаёт тикет с указанием:
   - Ссылка на Figma frame
   - Acceptance criteria
   - Оценка сложности

## Design System

Наш design system поддерживается в Figma:

- **Colors:** Brand palette, семантические цвета (success, error, warning)
- **Typography:** Заголовки, основной текст, подписи
- **Components:** Кнопки, поля ввода, карточки, модалки — используй существующие компоненты, когда возможно
- **Icons:** Набор Lucide

!!! warning "Не изобретай компоненты"
    Если компонент уже есть в design system — используй его. Если нужен новый — обсуди с дизайнером.

## Инструменты

- **Figma:** Основной инструмент дизайна — [командное пространство](https://figma.com)
- **Whimsical:** Флоучарты и wireframes
- **Zeplin:** Legacy-ссылки на проекты (мигрируем в Figma)
