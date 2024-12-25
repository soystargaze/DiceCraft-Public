# DiceCraft
**DiceCraft** es un proyecto modular para Minecraft que introduce mecánicas de combate inspiradas en sistemas de rol clásicos, como *Dungeons & Dragons*.

![Banner Logo](https://cdn.modrinth.com/data/MrR8fKPi/images/616c4847a32c8cf941ea3127cd4b4875e65b06a0.png)
---

## Características principales

### **Fabric Mod**
- **Tiradas de dados para ataques**: Los jugadores realizan tiradas de *d20* al atacar, determinando el éxito del ataque según la armadura del objetivo.
- **Bonificaciones por armas**: Cada arma tiene un bonificador que influye en las tiradas de ataque y daño.
- **Daño personalizado**: El daño infligido se calcula con tiradas de dados específicos para cada tipo de arma (por ejemplo, `d4` para ataques básicos, `d12` para armas avanzadas).
- **Soporte para mobs**:
    - Los mobs también realizan tiradas de ataque contra los jugadores, añadiendo un nivel de aleatoriedad al combate.
    - **Dados de daño específicos**: Cada tipo de mob tiene dados de daño configurables que determinan el daño que infligen (por ejemplo, `d6` para zombis, `d8` para esqueletos).
    - **FairMode**: Los mobs obtienen un bono adicional configurable (+5 por defecto) cuando atacan a jugadores con más de 20 puntos de armadura.
- **Bono de armadura con escudo**: Los jugadores reciben un bono adicional de armadura al llevar un escudo en la mano secundaria.
- **Comandos avanzados**:
    - **Añadir armas personalizadas**: Usa `/dicecraft addweapondamage <dado de daño> <bonus>` para incluir armas de otros mods con tiradas personalizadas.
    - **Añadir mobs personalizados**: Usa `/dicecraft addcustomentity <id_entidad> <dado de daño>` para configurar mobs de otros mods con tiradas personalizadas.
- **Configuración avanzada**:
    - Modifica las tiradas de daño, bonos y valores de armadura en los archivos de configuración del mod.
    - Ajusta las mecánicas del combate para un equilibrio personalizado.
- **Soporte multilingüe**: Traducciones completas al inglés y español, con planes para expandir a más idiomas.

### **Paper Plugin *(en desarrollo)***
- **Compatibilidad con servidores Paper**: Extiende las mecánicas del mod para servidores multijugador.
- **Configuración avanzada** *(en desarrollo)*:
    - Ajustes en el daño según el tipo de mob.
    - Efectos especiales basados en los resultados de las tiradas.

---

## Instalación

### **Requisitos Previos**
- Minecraft 1.21.1 o 1.21.4+.
- [Fabric Loader](https://fabricmc.net/use) y [Fabric API](https://modrinth.com/mod/fabric-api) para el mod.
- Un servidor Paper para el plugin.

---

## Uso

### **Jugadores**
- Realiza un ataque normal con cualquier arma. Las mecánicas del mod calcularán automáticamente:
    - La tirada de ataque (*d20*).
    - Bonificaciones según el arma utilizada.
    - El daño infligido basado en la tirada de dados correspondiente.
Todo es configurable.

### **Mobs**
- Los mobs realizan tiradas de ataque (*d20*) para determinar si sus ataques tienen éxito.
- Cada mob tiene dados de daño configurables para calcular el daño infligido en un ataque exitoso.

### **FairMode**
- Los mobs obtienen un bono adicional configurable (+5 por defecto) cuando atacan a jugadores con más de 20 puntos de armadura.

### **Administradores**
- Usa comandos para añadir configuraciones personalizadas de armas y mobs:
    - `/dicecraft addweapondamage <dado de daño> <bono>`: Añade un arma con dados de daño y bono personalizado.
    - `/dicecraft addcustomentity <id_entidad> <dado de daño>`: Añade un mob con dados de daño personalizados.
- Modifica el archivo de configuración del mod para ajustar todos los aspectos del sistema de combate.

---

## Ejemplo de mecánicas

1. **Jugador ataca a un mob**:
    - Se realiza una tirada de ataque con un *d20*:
      ```
      Tirada de ataque: 15 + bonificador del arma.
      Valor de armadura del mob: 14.
      ```
    - Si la tirada supera el valor de armadura, el ataque tiene éxito.
    - Luego, se realiza una tirada de daño basada en el arma:
      ```
      Daño infligido: 1d8 (espada de hierro) → Resultado: 6.
      ```

2. **Mob ataca a un jugador**:
    - El mob realiza una tirada de ataque con un *d20* (incluyendo el bono de FairMode, si aplica).
    - Si la tirada supera la armadura del jugador, el ataque tiene éxito.
    - El daño se determina con un dado específico configurado para el mob:
      ```
      Daño infligido por zombi: 1d6 → Resultado: 4.
      ```

---

<details><summary>English</summary>

# DiceCraft

**DiceCraft** is a modular project for Minecraft that introduces combat mechanics inspired by classic role-playing systems, such as *Dungeons & Dragons*.

![Banner Logo](https://cdn.modrinth.com/data/MrR8fKPi/images/616c4847a32c8cf941ea3127cd4b4875e65b06a0.png)
---

## Main Features

### **Fabric Mod**
- **Attack Dice Rolls**: Players roll a *d20* when attacking, determining the success of the attack based on the target's armor.
- **Weapon Bonuses**: Each weapon has a bonus that influences both attack rolls and damage rolls.
- **Custom Damage**: Damage dealt is calculated using specific dice rolls for each weapon type (e.g., `d4` for basic attacks, `d12` for advanced weapons).
- **Mob Support**:
    - Mobs also roll attack dice against players, adding an element of randomness to combat.
    - **Specific Damage Dice**: Each mob type has configurable damage dice that determine the damage they deal (e.g., `d6` for zombies, `d8` for skeletons).
    - **FairMode**: Mobs gain an additional configurable bonus (+5 by default) when attacking players with more than 20 armor points.
- **Shield Armor Bonus**: Players receive an additional armor bonus when holding a shield in their offhand.
- **Advanced Commands**:
    - **Add Custom Weapons**: Use `/dicecraft addweapondamage <damage dice> <bonus>` to include weapons from other mods with custom rolls.
    - **Add Custom Mobs**: Use `/dicecraft addcustomentity <entity_id> <damage dice>` to configure mobs from other mods with custom rolls.
- **Advanced Configuration**:
    - Modify damage rolls, bonuses, and armor values in the mod’s configuration files.
    - Customize combat mechanics for better balance.
- **Multilingual Support**: Full translations in English and Spanish, with plans to expand to more languages.

### **Paper Plugin *(in development)***
- **Paper Server Compatibility**: Extends the mod’s mechanics to multiplayer servers.
- **Advanced Configuration** *(in development)*:
    - Adjust damage based on mob types.
    - Special effects based on dice roll outcomes.

---

## Installation

### **Requirements**
- Minecraft 1.21.1 or 1.21.4+.
- [Fabric Loader](https://fabricmc.net/use) and [Fabric API](https://modrinth.com/mod/fabric-api) for the mod.
- A Paper server for the plugin.

---

## Usage

### **Players**
- Perform a normal attack with any weapon. The mod’s mechanics will automatically calculate:
    - The attack roll (*d20*).
    - Bonuses based on the weapon used.
    - The damage dealt based on the corresponding dice roll.
Everything is configurable.

### **Mobs**
- Mobs perform attack rolls (*d20*) to determine if their attacks hit.
- Each mob has configurable damage dice to calculate the damage dealt on a successful attack.

### **FairMode**
- Mobs gain an additional configurable bonus (+5 by default) when attacking players with more than 20 armor points.

### **Administrators**
- Use commands to add custom weapon and mob configurations:
    - `/dicecraft addweapondamage <damage dice> <bonus>`: Add a weapon with custom damage dice and bonus.
    - `/dicecraft addcustomentity <entity_id> <damage dice>`: Add a mob with custom damage dice.
- Modify the mod's configuration file to adjust all aspects of the combat system.

---

## Example Mechanics

1. **Player attacks a mob**:
    - An attack roll with a *d20* is made:
      ```
      Attack roll: 15 + weapon bonus.
      Mob armor value: 14.
      ```
    - If the roll exceeds the armor value, the attack succeeds.
    - Then, a damage roll based on the weapon is made:
      ```
      Damage dealt: 1d8 (iron sword) → Result: 6.
      ```

2. **Mob attacks a player**:
    - The mob rolls an attack with a *d20* (including the FairMode bonus, if applicable).
    - If the roll exceeds the player’s armor, the attack succeeds.
    - Damage is determined with a specific dice roll configured for the mob:
      ```
      Damage dealt by zombie: 1d6 → Result: 4.
      ```

---

</details>
