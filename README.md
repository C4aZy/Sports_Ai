# Sports_Ai
ai to help make planer for sports trianing with recmmemadtions for injuries as well
# 🏆 Sports Training AI - Personalized Training Plan Generator

An intelligent training plan generator that creates personalized workout programs for 5 different sports, with injury-aware exercise filtering.

## 🎯 Features

- ✅ **5 Sports Supported**: Badminton, Basketball, Tennis, Cricket, Football
- ✅ **70+ Exercises**: Sport-specific exercise database
- ✅ **Injury Management**: Automatically filters exercises based on 9 injury types
- ✅ **3 Difficulty Levels**: Beginner, Intermediate, Advanced
- ✅ **Multiple Goals**: Power, Strength, Endurance, Agility, Overall
- ✅ **Flexible Scheduling**: 3-6 days per week
- ✅ **Personalized Recommendations**: Sets, reps, rest times adapted to your level
- ✅ **Save Plans**: Export to text files

## 📁 Project Structure

```
training-ai/
├── data/
│   └── sports_exercises.csv       # Exercise database
├── src/
│   ├── sports_plan_generator.py   # Core AI engine
│   └── interactive_injury_planner.py  # Interactive interface
├── tests/
│   └── test_database.py           # Database verification
├── plans/
│   └── (saved plans)              # Generated training plans
├── create_database.py             # Database creator
└── README.md                      # This file
```

## 🚀 Quick Start

### 1. Install Requirements

```bash
pip install pandas
```

### 2. Create Exercise Database

```bash
python create_database.py
```

This creates `data/sports_exercises.csv` with 70+ exercises.

### 3. Verify Database (Optional)

```bash
python tests/test_database.py
```

### 4. Generate Your Training Plan

**Interactive Mode (Recommended):**
```bash
python src/interactive_injury_planner.py
```

**Programmatic Mode:**
```bash
python src/sports_plan_generator.py
```

## 💡 Usage Examples

### Example 1: Basketball Player - No Injuries

```python
from src.sports_plan_generator import SportsTrainingGenerator

generator = SportsTrainingGenerator('data/sports_exercises.csv')

user_profile = {
    'sport': 'Basketball',
    'fitness_level': 'Intermediate',
    'goal': 'Power',
    'days_per_week': 4,
    'session_duration': 60,
    'equipment_available': ['Bodyweight', 'Dumbbell'],
    'injuries': []
}

plan = generator.generate_plan(user_profile)
generator.print_plan(plan)
```

### Example 2: Tennis Player - Shoulder Injury

```python
user_profile = {
    'sport': 'Tennis',
    'fitness_level': 'Beginner',
    'goal': 'Overall',
    'days_per_week': 3,
    'session_duration': 60,
    'equipment_available': ['Bodyweight', 'Resistance Band'],
    'injuries': ['shoulder']  # Filters out overhead exercises
}

plan = generator.generate_plan(user_profile)
generator.print_plan(plan)
```

## 🏥 Supported Injuries

The AI can accommodate and provide safe exercises for:

1. **Knee** - ACL, MCL, meniscus, patellar tendon
2. **Shoulder** - Rotator cuff, impingement
3. **Lower Back** - Lumbar strain, disc issues
4. **Ankle** - Sprains, Achilles tendon
5. **Wrist** - Sprains, carpal tunnel
6. **Elbow** - Tennis elbow, tendonitis
7. **Hip** - Flexor strain, labral tears
8. **Upper Back/Neck** - Thoracic pain
9. **Groin** - Adductor strain

## 📊 What Gets Generated

For each user, the AI creates:

- **Weekly Workout Schedule** (3-6 days)
- **Sport-Specific Exercises** (filtered by injury)
- **Sets, Reps, Rest Times** (adapted to fitness level)
- **Warm-up & Cool-down** (for each session)
- **Injury Management Tips** (if applicable)
- **Progression Strategy** (10+ week plan)

## 🧠 How It Works

### 1. Data Collection
- 70+ exercises with metadata (sport, difficulty, equipment, body parts)

### 2. Rule-Based Filtering
- Sport matching
- Difficulty level matching
- Injury-based filtering (smart body part mapping)
- Equipment availability

### 3. Intelligent Plan Generation
- Weekly structure based on training frequency
- Exercise selection from filtered pool
- Sets/reps assignment based on goal and level
- Rest time calculation

### 4. Safety Checks
- Exercises mapped to affected body parts
- Keyword detection (jump, squat, overhead, etc.)
- Automatic exclusion of risky exercises
- Professional consultation reminders

## 🎨 Customization

### Add More Exercises

Edit `data/sports_exercises.csv` or modify `create_database.py`:

```python
["New Exercise", "Muscle", "Equipment", "Difficulty", "Type", "Sport", "Description", "Focus"]
```

### Add More Sports

Edit `sport_focus` dictionary in `sports_plan_generator.py`:

```python
sport_focus = {
    'YourSport': ['Focus1', 'Focus2', 'Focus3', 'Focus4']
}
```

### Modify Sets/Reps

Edit `_get_sets_reps()` method in `sports_plan_generator.py
