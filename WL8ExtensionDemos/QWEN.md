# QWEN.md — Контекст проекта SystemsCreator.WL8Extension (WL8ExtensionDemos)

## 📋 Обзор проекта

**WL8ExtensionDemos** — это библиотека расширений для Wealth-Lab 8, содержащая набор пользовательских индикаторов технического анализа, extension methods, Position Score Cards и пример клиентского расширения с дочерним WPF-окном.

Проект основан на открытой библиотеке **WL8ExtensionDemos** от Quantacula, LLC и используется как учебная база для создания собственных расширений Wealth-Lab 8.

### Назначение

- Создание пользовательских индикаторов технического анализа для Wealth-Lab 8
- Разработка extension methods для расширения функциональности Wealth-Lab
- Создание пользовательских Position Score Cards для оценки позиций
- Разработка клиентских расширений с собственными UI-окнами (Child Windows)

---

## 🏗️ Архитектура проекта

### Структура каталогов

```
WL8ExtensionDemos/
├── WL8ExtensionDemos.csproj       # Проект библиотеки (.NET 8.0)
├── QWEN.md                        # Этот файл контекста
├── Indicators/                    # Пользовательские индикаторы (9 файлов)
│   ├── HiLoLimit.cs               # Беззапаздывающий лимит (Dr.Koch)
│   ├── MansfieldRelativeStrength.cs # Индикатор относительной силы (Springroll)
│   ├── MinerviniTrendRatio.cs     # Коэффициент тренда Minervini
│   ├── PctOffATH.cs               # Процент от исторического максимума
│   ├── RealRelativeStrength.cs    # Реальная относительная сила
│   ├── RsiWilliamsVixFix.cs       # RSI Williams VIX Fix
│   ├── SwingHi.cs                 # Свинг-хаи (локальные максимумы)
│   ├── SwingLo.cs                 # Свинг-лоу (локальные минимумы)
│   └── SwingHiLo.cs               # Комбинированный свинг-индикатор
│
├── ExtensionMethods/              # Методы расширения
│   ├── PositionExtensions.cs      # Расширения для класса Position
│   └── CosmeticExtensions.cs      # Косметические расширения
│
├── PositionScoreCards/            # Position Score Cards
│   └── DemoPositionScoreCard.cs   # Пример метрики StdDevReturns
│
├── ClientExtension/               # Клиентское расширение
│   └── WL8DemosClientExtension.cs # Добавляет пункт меню в Wealth-Lab 8
│
├── ChildWindows/                  # Дочерние окна WPF
│   ├── DemoChildWindow.xaml       # Разметка окна
│   └── DemoChildWindow.xaml.cs    # Код окна
│
├── Glyphs/                        # Иконки для UI
│   └── Demo.png                   # Иконка для меню расширения
│
└── bin/                           # Скомпилированные файлы
└── obj/                           # Промежуточные файлы сборки
```

### Компоненты библиотеки

#### 1. Индикаторы (`Indicators/`)

Все индикаторы наследуются от `IndicatorBase` и расположены в namespace `WealthLab.Community`:

| Индикатор | Описание | Автор |
|-----------|----------|-------|
| `HiLoLimit` | Беззападывающий лимит на основе максимальных/минимальных уровней | Dr.Koch |
| `MansfieldRelativeStrength` | Индикатор относительной силы Mansfield | Springroll |
| `MinerviniTrendRatio` | Коэффициент тренда Minervini | — |
| `PctOffATH` | Процент от исторического максимума (All-Time High) | — |
| `RealRelativeStrength` | Реальная относительная сила | — |
| `RsiWilliamsVixFix` | RSI Williams VIX Fix | — |
| `SwingHi` | Свинг-хаи (локальные максимумы) | — |
| `SwingLo` | Свинг-лоу (локальные минимумы) | — |
| `SwingHiLo` | Комбинированный свинг-индикатор | — |

#### 2. Методы расширения (`ExtensionMethods/`)

- **`PositionExtensions`** — расширения для класса `Position`:
  - `BarByBarReturns()` — возвращает `TimeSeries` с процентной доходностью бар за баром

- **`CosmeticExtensions`** — косметические расширения для UI

#### 3. Position Score Cards (`PositionScoreCards/`)

- **`DemoPositionScoreCard`** — пример метрики оценки позиций:
  - `StdDevReturns` — стандартное отклонение доходности позиции

#### 4. Клиентское расширение (`ClientExtension/`)

- **`WL8DemosClientExtension`** — главное расширение, добавляющее пункт меню "Demo Extension" в Wealth-Lab 8

#### 5. Дочерние окна (`ChildWindows/`)

- **`DemoChildWindow`** — пример WPF окна для выбора и отображения индикаторов

---

## 🛠️ Технологии и зависимости

### Основные технологии

- **Язык**: C# (.NET 8.0)
- **Платформа**: .NET 8.0 Windows 7.0+
- **UI фреймворк**: WPF (Windows Presentation Foundation)
- **IDE**: Visual Studio 2022 / Visual Studio 2026

### Зависимости Wealth-Lab 8

Библиотека использует следующие DLL Wealth-Lab (установлены в `C:\Program Files\Quantacula, LLC\WealthLab 8\`):

```xml
<WealthLab.ChartWPF>
<WealthLab.Core>
<WealthLab.WPF>
```

### Пространства имён

Основные namespace, используемые в проекте:

```csharp
using WealthLab.Backtest;
using WealthLab.Core;
using WealthLab.Indicators;
using WealthLab.WPF;
using WealthLab.Data;
using WealthLab.Community;  // Для индикаторов
```

---

## 🚀 Сборка и развёртывание

### Требования

- **ОС**: Windows 10/11
- **.NET**: .NET 8.0 SDK
- **Wealth-Lab 8**: установлен в `C:\Program Files\Quantacula, LLC\WealthLab 8\`
- **Visual Studio**: 2022 или 2026 с поддержкой .NET и WPF

### Сборка проекта

```powershell
# Перейти в директорию решения
cd C:\Users\vdv-v\source\repos\SystemsCreator.WL8Extension\WL8ExtensionDemos

# Сборка через dotnet CLI
dotnet build WL8ExtensionDemos.csproj --configuration Release
```

### Установка в Wealth-Lab 8

1. **Собрать библиотеку** в режиме Release
2. **Скопировать DLL** из `bin/Release/` в папку установки Wealth-Lab 8:
   ```
   C:\Program Files\Quantacula, LLC\WealthLab 8\
   ```
3. **Разблокировать файл** (если требуется):
   - Правой кнопкой на DLL → Properties → Unblock
4. **Перезапустить Wealth-Lab 8**

После установки индикаторы появятся в папке **Community**.

### Использование в стратегиях

Добавить директиву `using` в начало файла стратегии:

```csharp
using WealthLab.Backtest;
using WealthLab.Core;
using WealthLab.Community;  // Для индикаторов

namespace WealthScript2
{
    public class MyStrategy : UserStrategyBase
    {
        public override void Initialize(BarHistory bars)
        {
            // Пример использования индикатора HiLoLimit
            PlotIndicator(new HiLoLimit(bars, 14, 2.00, 2.00), 
                         WLColor.FromArgb(255, 0, 0, 255), 
                         PlotStyle.Line);
        }

        public override void Execute(BarHistory bars, int idx)
        {
            // Логика стратегии
        }
    }
}
```

### Примеры использования компонентов

#### Индикатор Mansfield Relative Strength

```csharp
var mrs = MansfieldRelativeStrength.Series(bars, "$NDX", 200);
PlotIndicator(mrs, WLColor.CornflowerBlue, PlotStyle.Line);
```

#### Extension method для Position

```csharp
// Получить доходность бар за баром
TimeSeries returns = pos.BarByBarReturns();
```

#### Position Score Card

```csharp
// В настройках бэктеста выбрать "Demo Position ScoreCard"
// Метрика: StdDevReturns
```

---

## 📝 Практики разработки

### Создание нового индикатора

```csharp
using WealthLab.Core;
using WealthLab.Indicators;

namespace WealthLab.Community
{
    public class MyIndicator : IndicatorBase
    {
        public MyIndicator() : base() { }

        public MyIndicator(BarHistory source, int period) : base()
        {
            Parameters[0].Value = source;
            Parameters[1].Value = period;
            Populate();
        }

        public static MyIndicator Series(BarHistory source, int period)
        {
            string key = CacheKey("MyIndicator", period);
            if (source.Cache.ContainsKey(key))
                return (MyIndicator)source.Cache[key];
            MyIndicator indicator = new MyIndicator(source, period);
            source.Cache[indicator] = indicator;
            return indicator;
        }

        public override string Name => "My Indicator";
        public override string Abbreviation => "MYIND";
        public override string HelpDescription => "Описание индикатора";
        public override string PaneTag => "Price";
        public override WLColor DefaultColor => WLColor.Blue;

        public override void Populate()
        {
            BarHistory source = Parameters[0].AsBarHistory;
            int period = Parameters[1].AsInt;
            DateTimes = source.DateTimes;

            // Логика расчёта индикатора
            for (int bar = period; bar < source.Count; bar++)
            {
                Values[bar] = /* расчёт */;
            }
        }

        protected override void GenerateParameters()
        {
            AddParameter("Source", ParameterType.BarHistory, null);
            AddParameter("Period", ParameterType.Int32, 14);
        }
    }
}
```

### Создание extension method

```csharp
using WealthLab.Backtest;
using WealthLab.Core;

namespace WL8ExtensionDemos
{
    public static class PositionExtensions
    {
        public static TimeSeries MyExtensionMethod(this Position pos)
        {
            // Расширение функциональности Position
            TimeSeries ts = new TimeSeries();
            // Логика...
            return ts;
        }
    }
}
```

### Создание Position Score Card

```csharp
using WealthLab.Backtest;
using WealthLab.Core;

namespace WL8ExtensionDemos
{
    public class MyScoreCard : PositionScoreCardBase
    {
        public override string Name => "My Score Card";
        public override List<string> PositionMetricNames => _names;

        public override double CalculatePositionMetric(
            Backtester bt, Position pos, string metricName)
        {
            switch(metricName)
            {
                case "MyMetric":
                    // Расчёт метрики
                    return result;
                default:
                    return Double.NaN;
            }
        }

        public override bool ColorizeMetric(string metric) => false;
        public override int DecimalsMetric(string metric) => 2;

        private static List<string> _names = new List<string>() { "MyMetric" };
    }
}
```

### Создание клиентского расширения

```csharp
using System.Windows;
using System.Windows.Controls;
using System.Windows.Media;
using WealthLab.WPF;

namespace WL8ExtensionDemos
{
    public class MyClientExtension : WL8ClientExtensionBase
    {
        public override string Name => "MyExtension";

        public override List<MenuItem> GetMenuItems()
        {
            List<MenuItem> mi = new List<MenuItem>();
            MenuItem mni = CreateExtensionMenuItem("My Menu", GetGlyph(), mniClick);
            mi.Add(mni);
            return mi;
        }

        private void mniClick(object sender, RoutedEventArgs e)
        {
            MyChildWindow window = new MyChildWindow();
            MyClientHost.ShowExtensionChildWindow(window, "My Window", GetGlyph());
        }

        private ImageSource GetGlyph()
        {
            return GlyphManager.GetImageSource(
                "WL8ExtensionDemos.Glyphs.MyIcon.png", this);
        }
    }
}
```

---

## 🔧 Конфигурация и переменные окружения

### Пути к Wealth-Lab 8

По умолчанию проект ссылается на Wealth-Lab 8, установленный в:

```
C:\Program Files\Quantacula, LLC\WealthLab 8\
```

Если Wealth-Lab установлен в другую папку, обновить пути в `.csproj`:

```xml
<Reference Include="WealthLab.Core">
  <HintPath>Путь\К\WealthLab.Core.dll</HintPath>
</Reference>
```

### Версии

- **Версия библиотеки**: 8.0.3
- **Target Framework**: net8.0-windows7.0
- **Платформы**: AnyCPU, x64

---

## 🐛 Отладка и решение проблем

### Частые проблемы

1. **DLL не загружается в Wealth-Lab**
   - Проверить, разблокирован ли файл (Properties → Unblock)
   - Убедиться, что DLL скопирована в правильную папку
   - Проверить совместимость версий .NET

2. **Ошибки сборки**
   - Убедиться, что Wealth-Lab 8 установлен
   - Проверить пути к DLL в `.csproj`
   - Очистить решение: `dotnet clean`
   - Восстановить пакеты: `dotnet restore`
   - Пересобрать: `dotnet build`

3. **Индикатор не отображается в списке**
   - Проверить namespace (должен быть `WealthLab.Community`)
   - Убедиться, что класс наследуется от `IndicatorBase`
   - Перезапустить Wealth-Lab

### Логирование

Для отладки использовать `WLHost.Instance` для вывода сообщений:

```csharp
WLHost.Instance.Alert("Сообщение для отладки");
```

---

## 📚 Дополнительные ресурсы

### Внутренняя документация

- **Исходный код**: Примеры в папках `Indicators/`, `ExtensionMethods/`, `PositionScoreCards/`

### Внешние ресурсы

- **Wealth-Lab Official**: https://www.wealth-lab.com/
- **Wealth-Lab Documentation**: https://www.wealth-lab.com/docs
- **Quantacula GitHub**: https://github.com/Quantacula

### Связанные проекты пользователя

- **TrendTeamTrading**: Основные стратегии и хендлеры
- **WealthLabStrategies**: Стратегии для Wealth-Lab 8 в составе TrendTeamTrading
- **TaLib.TrendTeam**: Библиотека технического анализа TALib

---

## 📊 Структура проекта (детали)

### Файлы проекта

| Файл | Назначение |
|------|------------|
| `WL8ExtensionDemos.csproj` | Проект библиотеки (.NET 8.0) |
| `Indicators/*.cs` | Исходный код индикаторов (9 файлов) |
| `ExtensionMethods/*.cs` | Методы расширения (2 файла) |
| `PositionScoreCards/*.cs` | Position Score Cards (1 файл) |
| `ClientExtension/*.cs` | Клиентское расширение (1 файл) |
| `ChildWindows/*.xaml + .cs` | Дочерние окна WPF (2 файла) |
| `Glyphs/*.png` | Иконки для UI |

### Ключевые классы

```
IndicatorBase (базовый класс)
├── HiLoLimit
├── MansfieldRelativeStrength
├── MinerviniTrendRatio
├── PctOffATH
├── RealRelativeStrength
├── RsiWilliamsVixFix
├── SwingHi
├── SwingLo
└── SwingHiLo

PositionScoreCardBase (базовый класс)
└── DemoPositionScoreCard

WL8ClientExtensionBase (базовый класс)
└── WL8DemosClientExtension

ChildWindow (базовый класс WPF)
└── DemoChildWindow
```

---

## 🎯 Типичные сценарии использования

### 1. Добавление нового индикатора

```powershell
# 1. Создать файл индикатора в Indicators/
# 2. Наследоваться от IndicatorBase
# 3. Реализовать Populate() и GenerateParameters()
# 4. Собрать: dotnet build
# 5. Скопировать DLL в Wealth-Lab 8
# 6. Перезапустить Wealth-Lab
```

### 2. Создание extension method

```powershell
# 1. Создать static класс в ExtensionMethods/
# 2. Добавить static метод с this-параметром
# 3. Собрать и скопировать DLL
# 4. Использовать в стратегиях через using
```

### 3. Разработка Position Score Card

```powershell
# 1. Создать класс в PositionScoreCards/
# 2. Наследоваться от PositionScoreCardBase
# 3. Реализовать CalculatePositionMetric()
# 4. Собрать и протестировать в бэктесте
```

---

*Последнее обновление: 8 марта 2026 г.*
