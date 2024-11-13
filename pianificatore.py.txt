# Input: lista di lavoratori con disponibilità e ore settimanali richieste
team = [
    {"name": "Luca", "availability": ["Monday", "Wednesday", "Friday"], "hours": 20},
    {"name": "Maria", "availability": ["Tuesday", "Thursday"], "hours": 15},
    {"name": "Sara", "availability": ["Monday", "Tuesday", "Wednesday"], "hours": 10},
]

# Giorni della settimana
week_days = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday"]

# Inizializza i turni
schedule = {day: [] for day in week_days}

# Funzione semplice per assegnare i turni
for member in team:
    assigned_hours = 0
    for day in member["availability"]:
        if assigned_hours < member["hours"]:
            schedule[day].append(member["name"])
            assigned_hours += 8  # Si ipotizza turno di 8 ore

# Output della pianificazione
for day, workers in schedule.items():
    print(f"{day}: {', '.join(workers) if workers else 'No shifts assigned'}")
