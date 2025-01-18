<details><summary>English</summary>

# DiceCraft
**DiceCraft** is a modular project for Minecraft that introduces combat mechanics inspired by classic role-playing systems, such as *Dungeons & Dragons*.

![Discord](https://img.shields.io/discord/1079917552588816484?label=Discord&logo=discord&logoColor=white&color=6d1166&style=for-the-badge) ![](https://img.shields.io/badge/Made%20with-%E2%9D%A4%EF%B8%8F%20by%20stargaze-6d1166?style=for-the-badge)

![Banner Logo](https://cdn.modrinth.com/data/MrR8fKPi/images/bcdb4d4ec3756551118e01224bc99da5f230fdab.png)
---

## Main Features

### **Fabric**
<details><summary>Mod</summary>

- **Dice rolls for attacks**: Players perform *d20* rolls when attacking, determining the success of the attack based on the target's armor.
- **Weapon bonuses**: Each weapon has a bonus that influences attack and damage rolls.
- **Custom damage**: Damage dealt is calculated using dice rolls specific to each weapon type (e.g., `d4` for basic attacks, `d12` for advanced weapons).
- **Mob support**:
    - Mobs also roll for attacks against players, adding a level of randomness to combat.
    - **Specific damage dice**: Each mob type has configurable damage dice determining the damage they deal (e.g., `d6` for zombies, `d8` for skeletons).
    - **FairMode**: Mobs gain a configurable bonus (+5 by default) when attacking players with more than 20 armor points.
- **Armor bonus with shields**: Players receive an additional armor bonus when holding a shield in their off-hand.
- **Customizable dice rolls**:
    - **Public rolls**: Use `/dicecraft roll <dice>` or `/dc roll <dice>` to make a public roll visible to all players.
    - **Private rolls**: Use `/dicecraft proll <dice>` or `/dc proll <dice>` to make a private roll visible only to you.
    - Supported formats:
        - `dX`: A single die with X sides.
        - `NdX`: N dice with X sides.
        - `NdX+Y`: N dice with X sides plus a bonus Y.
    - Examples:
        - `/dicecraft roll d20`: Rolls a 20-sided die publicly.
        - `/dc roll 3d8+4`: Rolls three 8-sided dice with a bonus of +4 publicly.
        - `/dicecraft proll 2d6`: Rolls two 6-sided dice privately.
- **Advanced commands**:
    - **Add custom weapons**: Use `/dicecraft addweapondamage <damage dice> <bonus>` to include weapons from other mods with custom rolls.
    - **Add custom mobs**: Use `/dicecraft addcustomentity <mod:entity_id> <damage dice> <armor>` to configure mobs from other mods with custom rolls.
- **Alias support**:
    - All commands available under `dicecraft` can also be used with the alias `dc`.
    - Examples:
        - `/dicecraft roll d20` is equivalent to `/dc roll d20`.
        - `/dicecraft addcustomentity mod:zombie 6 15` is equivalent to `/dc addcustomentity mod:zombie 6 15`.
- **Advanced configuration**:
    - Modify damage rolls, bonuses, and armor values in the mod's configuration files.
    - Adjust combat mechanics for customized balance.
- **Multilingual support**: Fully translated into English and Spanish, with plans to expand to more languages.
</details>

---

### **Paper**
<details><summary>Plugin</summary>

- **Compatibility with Paper servers**: Extends the mod's mechanics for multiplayer servers.
- **Custom Attributes System**:
    - Players can manage their attributes using `/dicecraft stats <set|reset|view>`.
    - Admins can view other players' stats with `/dicecraft stats view <player>`.
- **Advanced commands**:
    - `/dicecraft config fairmode <true/false>`: Enables or disables FairMode.
    - `/dicecraft config shieldbonus <value>`: Adjusts the armor bonus provided by shields.
    - `/dicecraft config add weapon <damage die> <bonus>`: Add a custom weapon based on your model by having it in the mainhand.
    - `/dicecraft config add entity mythicmobs <mobname> <damage dice>`: Configures a MythicMobs entity with custom damage dice.
    - `/dicecraft config list mythicmobs`: Displays a list of available entities in MythicMobs.
    - `/dicecraft reload`: Reloads the plugin configuration.
    - `/dicecraft roll <dice>` or `/dc roll <dice>`: Perform a roll (e.g., `d20`, `3d6+4`).
    - `/dicecraft dmmode set <true/false>`: Enables or disables DM mode.
    - `/dicecraft dmmode status`: Shows the current DM mode status.
- **Customizable dice rolls**:
    - Use `/dicecraft roll <dice>` or `/dc roll <dice>` to make a public roll visible to all players.
    - Supported formats:
        - `dX`: A single die with X sides.
        - `NdX`: N dice with X sides.
        - `NdX+Y`: N dice with X sides plus a bonus Y.
    - Examples:
        - `/dicecraft roll d20`: Rolls a 20-sided dice.
        - `/dc roll 3d8+4`: Rolls three 8-sided dice with a bonus of +4.
        - `/dicecraft roll 2d6`: Rolls two 6-sided dice.
- **FairMode**:
    - Improves mob attacks against players with high armor values.
- **Integration with MythicMobs**:
    - Custom configuration for mobs created with MythicMobs.
- **Advanced configuration**:
    - Dynamic adjustments to damage and armor.
    - Support for custom weapon and mob models.
    - Support for custom MythicMobs entities.
    - Customizable combat mechanics.
    - Multilingual support.
    - Full customization of GUIs and messages.
</details>

---

## Installation

### **Requirements**
- Minecraft 1.21.1 or 1.21.4+.
- [Fabric Loader](https://fabricmc.net/use) and [Fabric API](https://modrinth.com/mod/fabric-api) for the mod.
- A Paper server for the plugin.

---

## Usage

### **Players**
- Perform a normal attack with any weapon. The mod will automatically calculate:
    - The attack roll (*d20*).
    - Bonuses based on the weapon used.
    - The damage dealt based on the corresponding dice roll.
      Everything is configurable.

### **Mobs**
- Mobs perform attack rolls (*d20*) to determine if their attacks succeed.
- Each mob has configurable damage dice to calculate the damage dealt on a successful attack.

### **FairMode**
- Mobs gain a configurable bonus (+5 by default) when attacking players with more than 20 armor points.

### **Administrators**
<details><summary>Fabric</summary>

- Use commands to add custom configurations for weapons and mobs:
    - `/dicecraft addweapondamage <damage dice> <bonus>` or `/dc addweapondamage <damage dice> <bonus>`: Adds a weapon with custom damage dice and bonus.
    - `/dicecraft addcustomentity <mod:entity_id> <damage dice> <armor>` or `/dc addcustomentity <mod:entity_id> <damage dice> <armor>`: Adds a mob with custom damage dice and armor.
    - `/dicecraft roll <dice>` or `/dc roll <dice>`: Perform a public roll (e.g., `d20`, `3d6+4`).
    - `/dicecraft proll <dice>` or `/dc proll <dice>`: Perform a private roll.
</details>

<details><summary>Paper</summary>

- Use commands to manage advanced configurations:
    - `/dicecraft stats <set|reset|view> [player]`: View or configure player attributes.
    - `/dicecraft config fairmode <true/false>`: Enables or disables FairMode.
    - `/dicecraft config shieldbonus <value>`: Adjusts the shield armor bonus.
    - `/dicecraft config add weapon <damage die> <bonus>`: Add a custom weapon based on your model by having it in the mainhand.
    - `/dicecraft config add entity mythicmobs <mobname> <damage dice>`: Configures custom mobs from MythicMobs.
    - `/dicecraft config list mythicmobs`: Lists entities from MythicMobs.
    - `/dicecraft reload`: Reloads the plugin configuration.
    - `/dicecraft roll <dice>` or `/dc roll <dice>`: Perform a roll (e.g., `d20`, `3d6+4`).
    - `/dicecraft dmmode set <true/false>`: Enables or disables DM mode.
    - `/dicecraft dmmode status`: Shows the current DM mode status.
</details>

---

## Example Mechanics

1. **Player attacks a mob**:
    - An attack roll is made with a *d20*:
      ```
      Attack Roll: 15 + weapon bonus.
      Mob Armor Value: 14.
      ```
    - If the roll exceeds the armor value, the attack succeeds.
    - Then, a damage roll is made based on the weapon:
      ```
      Damage Dealt: 1d8 (iron sword) → Result: 6.
      ```

2. **Mob attacks a player**:
    - The mob makes an attack roll with a *d20* (including the FairMode bonus, if applicable).
    - If the roll exceeds the player's armor, the attack succeeds.
    - Damage is determined with a specific die configured for the mob:
      ```
      Damage Dealt by Zombie: 1d6 → Result: 4.
      ```

---

## Support

If you need help or have questions, join our Discord server! 😊

</details>

# DiceCraft
**DiceCraft** es un proyecto modular para Minecraft que introduce mecánicas de combate inspiradas en sistemas de rol clásicos, como *Dungeons & Dragons*.

![Discord](https://img.shields.io/discord/1079917552588816484?label=Discord&logo=discord&logoColor=white&color=6d1166&style=for-the-badge) ![](https://img.shields.io/badge/Made%20with-%E2%9D%A4%EF%B8%8F%20by%20stargaze-6d1166?style=for-the-badge)

![Banner Logo](https://cdn.modrinth.com/data/MrR8fKPi/images/bcdb4d4ec3756551118e01224bc99da5f230fdab.png)
---

## Características principales

### **Fabric**
<details><summary>Mod</summary>

- **Tiradas de dados para ataques**: Los jugadores realizan tiradas de *d20* al atacar, determinando el éxito del ataque según la armadura del objetivo.
- **Bonificaciones por armas**: Cada arma tiene un bonificador que influye en las tiradas de ataque y daño.
- **Daño personalizado**: El daño infligido se calcula con tiradas de dados específicos para cada tipo de arma (por ejemplo, `d4` para ataques básicos, `d12` para armas avanzadas).
- **Soporte para mobs**:
    - Los mobs también realizan tiradas de ataque contra los jugadores, añadiendo un nivel de aleatoriedad al combate.
    - **Dados de daño específicos**: Cada tipo de mob tiene dados de daño configurables que determinan el daño que infligen (por ejemplo, `d6` para zombis, `d8` para esqueletos).
    - **FairMode**: Los mobs obtienen un bono adicional configurable (+5 por defecto) cuando atacan a jugadores con más de 20 puntos de armadura.
- **Bono de armadura con escudo**: Los jugadores reciben un bono adicional de armadura al llevar un escudo en la mano secundaria.
- **Tiradas de dados personalizables**:
    - **Tiradas públicas**: Usa `/dicecraft roll <dado>` o `/dc roll <dado>` para realizar una tirada pública visible para todos los jugadores.
    - **Tiradas privadas**: Usa `/dicecraft proll <dado>` o `/dc proll <dado>` para realizar una tirada privada visible solo para ti.
    - Formatos soportados:
        - `dX`: Un único dado de X caras.
        - `NdX`: N dados de X caras.
        - `NdX+Y`: N dados de X caras más un bono Y.
    - Ejemplos:
        - `/dicecraft roll d20`: Lanza un dado de 20 caras públicamente.
        - `/dc roll 3d8+4`: Lanza tres dados de 8 caras con un bono de +4 públicamente.
        - `/dicecraft proll 2d6`: Lanza dos dados de 6 caras en privado.
- **Comandos avanzados**:
    - **Añadir armas personalizadas**: Usa `/dicecraft addweapondamage <dado de daño> <bonus>` para incluir armas de otros mods con tiradas personalizadas.
    - **Añadir mobs personalizados**: Usa `/dicecraft addcustomentity <mod:id_entidad> <dado de daño> <armadura>` para configurar mobs de otros mods con tiradas personalizadas.
- **Soporte de alias**:
    - Todos los comandos disponibles bajo `dicecraft` también pueden usarse con el alias `dc`.
    - Ejemplos:
        - `/dicecraft roll d20` es equivalente a `/dc roll d20`.
        - `/dicecraft addcustomentity mod:zombie 6 15` es equivalente a `/dc addcustomentity mod:zombie 6 15`.
- **Configuración avanzada**:
    - Modifica las tiradas de daño, bonos y valores de armadura en los archivos de configuración del mod.
    - Ajusta las mecánicas del combate para un equilibrio personalizado.
- **Soporte multilingüe**: Traducciones completas al inglés y español, con planes para expandir a más idiomas.
</details>

---

### **Paper**
<details><summary>Plugin</summary>

- **Compatibilidad con servidores Paper**: Extiende las mecánicas del mod para servidores multijugador.
- **Sistema de Atributos Personalizados**:
    - Los jugadores pueden gestionar sus atributos con `/dicecraft stats <set|reset|view>`.
    - Los administradores pueden ver los atributos de otros jugadores con `/dicecraft stats view <player>`.
- **Comandos avanzados**:
    - `/dicecraft config fairmode <true/false>`: Activa o desactiva el modo FairMode.
    - `/dicecraft config shieldbonus <valor>`: Ajusta el bono de armadura otorgado por los escudos.
    - `/dicecraft config add weapon <dado de daño> <bonus>`: Añade un arma personalizada basada en su modelo teniéndola en la mano principal.
    - `/dicecraft config add entity mythicmobs <mobname> <dado de daño>`: Configura un mob de MythicMobs con dados de daño personalizados.
    - `/dicecraft config list mythicmobs`: Muestra una lista de entidades disponibles en MythicMobs.
    - `/dicecraft reload`: Recarga las configuraciones del plugin.
    - `/dicecraft roll <dado>` o `/dc roll <dado>`: Realiza una tirada pública (ej., `d20`, `3d6+4`).
    - `/dicecraft dmmode set <true/false>`: Activa o desactiva el modo DM.
    - `/dicecraft dmmode status`: Muestra el estado actual del modo DM.
- **Tiradas de dados personalizables**:
- Usa `/dicecraft roll <dado>` o `/dc roll <dado>` para realizar una tirada pública visible para todos los jugadores.
    - Formatos soportados:
        - `dX`: Un único dado de X caras.
        - `NdX`: N dados de X caras.
        - `NdX+Y`: N dados de X caras más un bono Y.
    - Ejemplos:
        - `/dicecraft roll d20`: Lanza un dado de 20 caras.
        - `/dc roll 3d8+4`: Lanza tres dados de 8 caras con un bono de +4.
        - `/dicecraft roll 2d6`: Lanza dos dados de 6 caras.
- **FairMode**:
    - Mejora los ataques de mobs contra jugadores con altos valores de armadura.
- **Integración con MythicMobs**:
    - Configuración personalizada para mobs creados con MythicMobs.
- **Configuración avanzada**:
    - Ajustes dinámicos de daño y armadura.
    - Soporte para modelos personalizados de armas y mobs.
    - Soporte para entidades personalizadas de MythicMobs.
    - Mecánicas de combate personalizables.
    - Soporte multilingüe.
    - Personalización completa de GUIs y mensajes.
</details>

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
<details><summary>Fabric</summary>

- Usa comandos para añadir configuraciones personalizadas de armas y mobs:
    - `/dicecraft addweapondamage <dado de daño> <bono>` o `/dc addweapondamage <dado de daño> <bono>`: Añade un arma con dados de daño y bono personalizado.
    - `/dicecraft addcustomentity <mob:id_entidad> <dado de daño>` o `/dc addcustomentity <mob:id_entidad> <dado de daño> <armadura>`: Añade un mob con dados de daño y armadura personalizadas.
    - `/dicecraft roll <dado>` o `/dc roll <dado>`: Realiza una tirada pública (ej., `d20`, `3d6+4`).
    - `/dicecraft proll <dado>` o `/dc proll <dado>`: Realiza una tirada privada.
</details>

<details><summary>Paper</summary>

- Usa comandos para gestionar configuraciones avanzadas:
    - `/dicecraft stats <set|reset|view> [player]`: Ver o configurar atributos de jugadores.
    - `/dicecraft config fairmode <true/false>`: Activa o desactiva el modo FairMode.
    - `/dicecraft config shieldbonus <valor>`: Ajusta el bono de armadura del escudo.
    - `/dicecraft config add weapon <dado de daño> <bonus>`: Añade un arma personalizada basada en su modelo teniéndola en la mano principal.
    - `/dicecraft config add entity mythicmobs <mobname> <dado de daño>`: Configura mobs personalizados desde MythicMobs.
    - `/dicecraft config list mythicmobs`: Lista las entidades de MythicMobs.
    - `/dicecraft reload`: Recarga las configuraciones del plugin.
    - `/dicecraft roll <dado>` o `/dc roll <dado>`: Realiza una tirada (ej., `d20`, `3d6+4`).
    - `/dicecraft dmmode set <true/false>`: Activa o desactiva el modo DM.
    - `/dicecraft dmmode status`: Muestra el estado actual del modo DM.
</details>

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

## Soporte

Si necesitas ayuda o tienes preguntas, ¡únete a nuestro servidor de Discord! 😊

--- 
