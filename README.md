# core-gruppe6

**Premium Gruppe 6 armored delivery job for FiveM** — QBCore / ESX / QBox compatible, React 19 NUI, TypeScript, Tailwind CSS.

---

## Features

- Armored cash delivery job with configurable delivery points
- React 19 NUI built with Vite + TypeScript + Tailwind CSS — zero jQuery, zero legacy HTML
- Live payload status (carrying bag / secured in truck)
- Delivery progress tracker synced to NUI in real time
- Configurable salary paid in cash or direct to bank
- Job lock — optionally restrict to `ambulance` job or open to all players
- Custom NPC job giver and vehicle spawn point via config
- Full locale table — every string is editable, no hardcoded UI text
- Hot-reload dev panel in browser (auto-hidden in FiveM)
- `fetchNui` utility with typed generics and graceful fallback
- `useNuiEvent` hook — clean, reusable NUI message listener

---

## Requirements

- FiveM server running **artifact 6116 or newer**
- Lua 5.4 enabled (`lua54 'yes'` — already set in manifest)
- Node.js **18+** and npm (for UI build only)
- QBCore **or** ESX **or** QBox framework (see [Configuration](#configuration))

---

## Installation

```
1. Drop the resource folder into your server's resources directory
2. Add `ensure core-gruppe6` to your server.cfg
3. Build the UI (see UI Build below)
4. Configure Script in config.lua, then restart the resource
```


## Configuration

All config lives in `config.lua` under the `Config` table.

### Job access

```lua
Config.JobName    = "ambulance"   -- framework job name to check
Config.JobRequired = false        -- true = job-locked, false = open to all
```

### Vehicle and NPC spawn

```lua
Config.Main = {
    vehicle_coords = vector4(-4.74, -670.57, 31.95, 187.08),
    vehicle_model  = "stockade",

    job_guy_coords = vector4(0.11, -665.72, 31.34, 184.91),
    job_guy_model  = "s_m_m_security_01"
}
```

### Salary

```lua
Config.Salary = {
    amount = 10000,
    type   = "cash"   -- "cash" or "bank"
}
```

### Delivery points

Add or remove as many entries as you want. Do not touch the `delivered` field — it is managed at runtime.

```lua
Config.DeliveryPoints = {
    {
        coords    = vector4(147.12, -1045.02, 29.37, 252.97),
        delivered = false
    },
    {
        coords    = vector4(-1211.24, -335.61, 37.78, 308.9),
        delivered = false
    }
}
```

### Locales

Every string displayed to players is editable here. Supports any language.

```lua
Config.Locales = {
    main_blip_name           = "Gruppe 6 Job",
    delivery_blip_name       = "Delivery Point",
    start_job_label          = "Start job",
    end_job_label            = "Return vehicle",
    repair_vehicle_label     = "Repair vehicle",
    get_cash_label           = "Take out cash bag",
    job_in_progress          = "Your job is currently in progress!",
    error                    = "Deliver one cash suitcase before taking out another one!",
    hint                     = "Press [E] to deliver cash",
    all_deliveries_completed = "All deliveries completed, return to base to return vehicle and get paid",
    deliveries_status        = "Deliveries completed: ",
    salary_received          = "You've received salary of $",
    error2                   = "Complete all deliveries to end your job!"
}
```

---

## Tech Stack

| Layer | Tech |
|---|---|
| UI framework | React 19 |
| Language | TypeScript 5.6 |
| Styling | Tailwind CSS 3.4 |
| Build tool | Vite 6 |
| Icons | lucide-react |
| NUI bridge | Custom `useNuiEvent` hook + `fetchNui` utility |
| Scripting | Lua 5.4 |

---

## Support

Open a ticket in the Core Forge Discord or post on the CFX.re thread linked on the Tebex page.

> **core-forge.tebex.io** · GitHub: **Core-Forge-5** · YouTube: **@CoreForgeFivem**