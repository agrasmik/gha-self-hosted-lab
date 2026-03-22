# 🚀 GitHub Actions Learning Lab: From Zero to CD

[Русский](#-github-actions-learning-lab-from-zero-to-cd) | [English](README.en.md)

Этот репозиторий — мой практический полигон для изучения GitHub Actions (GHA). 
**Цель:** пройти путь от простейшей автоматизации до полноценного CI/CD пайплайна с деплоем на собственный сервер.

--- 

## 🧭 Дорожная карта (Roadmap)
### Этап 1: Основы и CI (Continuous Integration)
- **Синтаксис YAML:** Структура воркфлоу (name, on, jobs, steps).
- **Контроль качества:** Настройка линтеров и автоматической сборки (dotnet build / pip install).
- **Тестирование:** Внедрение Unit-тестов и блокировка деплоя при их падении.
- **Artifacts:** Сохранение скомпилированных файлов через actions/upload-artifact.

### Этап 2: Контейнеризация и Безопасность
- **Docker:** Сборка образов внутри GHA.
- **Registry:** Пуш образов в GitHub Container Registry (GHCR).
- **Secrets:** Работа с зашифрованными переменными для доступа к Docker/SSH.

### Этап 3: Инфраструктура и CD (Continuous Deployment)
- **Self-hosted Runner:** Поднятие своего агента на виртуальной машине.
- **Vagrant:** Автоматизация развертывания среды раннера (Infrastructure as Code).
- **Deployment:** Автоматическое обновление приложения на сервере при пуше в main.

---

## 🛠 Системные требования (Prerequisites)

Для локальной отработки этапа с Self-hosted Runner потребуются:

| Инструмент | Миним. версия | Ссылка |
| :--- | :---: | :---:|
| Vagrant | 2.3 |[Установить](https://developer.hashicorp.com/vagrant/downloads)<br>[Быстрый старт](https://developer.hashicorp.com/vagrant/tutorials/get-started)
| VirtualBox | 7.0| [Скачать](https://www.virtualbox.org/) |
| Git | latest | [Скачать](https://git-scm.com/) | 

**Примечание по архитектуре:** 
- Использование Vagrant обусловлено максимальным исключением ***"It works on my machine"***.
- Если вы используете Apple Silicon (M1/M2) или другой ARM-процессор, потребуется адаптация под другую [архитектуру](https://developer.hashicorp.com/vagrant/docs/boxes).
- Проект ориентирован на провайдер *virtualbox*. Если вы используете другой - потребуется адаптация под Ваш [Провайдер](https://developer.hashicorp.com/vagrant/docs/providers).  

## 📚 Чек-лист тем для изучения🟢 

### Модуль 1: Базовая автоматизация
- [ ] Создание первого Workflow (hello-world.yml).
- [ ] Изучение триггеров: push, pull_request, workflow_dispatch.
- [ ] Использование Contexts (например, github.sha, github.ref).

### 🔵 Модуль 2: Continuous Integration (CI)
- [ ] Шаг сборки приложения.
- [ ] Запуск тестов и обработка ошибок.
- [ ] Параллельный запуск Job (Matrix Strategy).
- [ ] Оптимизация: Кэширование зависимостей (actions/cache).

### 🟠 Модуль 3: Docker и Артефакты
- [ ] Написание Dockerfile (Multi-stage).
- [ ] Логин и Пуш в GHCR.
- [ ] Передача данных между Jobs через Artifacts.

### 🔴 Модуль 4: Self-hosted & Deploy
- [ ] Настройка Vagrantfile для подготовки сервера.
- [ ] Установка и регистрация GitHub Runner в ОС.
- [ ] CD: Обновление контейнеров через docker-compose на своем сервере.

## ⚠️ Правила безопасности (Security Best Practices)

1. **Public Repo Warning:** Не используйте селф-хостед раннеры в публичных репозиториях без настройки *"Require approval for all outside collaborators"*
2. **No Root:** Запуск агента раннера должен производиться от имени выделенного пользователя, а не от root.
3. **Secrets:** Никогда не выводите секреты в консоль (логгирование).

*Создано для профессионального роста и освоения автоматизации.*