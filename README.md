# ADnD-2ed-AtS

This is a variation of the Advanced 2nd Edition (Simple Sheet) originally created by Dylan G. based on work by Stephen S. for use in roll20. Most of the attribute names have been preserved to allow for portability between the original character sheet and this version.

This version of the character sheet has been reworked and reorganized a great deal. It does not contain the "Monster Sheet" option nor many of the Skills & Powers attribute fields which the original contained. It does have support for psionics using the Skills and Powers rules with the relevant attributes added to the sheet.

This sheet also contains several new rolltemplates. They are all built with clean and easy to read styling, and color coded according to function:
  AtS_default - This is similar to the standard default template with an added property called {{desc}} which has a column span built into it so that the preceeding properties entered do not squeeze the description field into one side of the table which is created within the template. The AtS_default rolltemplate has a green header.
  AtS_Attack - This is uses graphical as well as text indicators to display the Armor class which an attack hits as well as damage dealt vs both Small/Medium targets as well as vs Large targets. It is designed to clearly display the attacker's name, their target, and which weapon they are using. It also will automatically display whether the attack was a critical hit or a fumble. The attack template has a red header.
  AtS_spell - This template is designed to clearly display the spell being cast, the spell level, and School or Sphere in the header, which is colored Blue. Immediately below the header it displays the six basic statistics of each spell, Components, Casting Time, Range, Duration, Area of Effect, and Saving Throw info. Below that are two optional attributes that will only be displayed if damage or healing are entered as properties. These optional sections are followed by an area to describe the spell's effects.

Macro format for using the AtS_default template:
    &{template:AtS_default}{{ name=<name or title desired> }} {{ <Any Property> = [[ roll ]] or <value> }}
    {{ <Any Property2...etc> = [[ roll ]] or <value> }} {{ desc = <description> }}

Note: you can enter as many custom properties as you like for your purposes, in this regard this template is exactly like the standard default template built into roll20. The "desc" property is customized for the sheet, and will always display after all of the other properties that you enter, even if you put it in the macro before your custom properties.

Macro format for using the AtS_attack template:
    &{template:AtS_attack} {{ attacker = @{selected|token_name} }} {{ target = @{target|token_name} }}
    {{weapon_used = @{selected|weaponname} }} {{ ac_hit = [[ <attack roll formula> ]] }}
    {{ dmg_s = [[ <roll formula for S/M targets> ]] }} {{ dmg_l = [[ <roll formula for Lg targets> ]] }}

The properties used for the attack template are {{attacker}}, {{target}}, {{weapon_used}}, {{ac_hit}}, {{dmg_s}}, {{dmg_l}}
Currently it does not support critical hit damage rolls as I don't use them in my campaign, but I intend to add that as an optional feature as most DM's do grant extra damage dice on critical hits. The properties to enter the bonus damage formulae for critical hits when implemented will be {{crit_s}} and {{crit_l}} and these will only display when a critical success is rolled.

Macro format for using the AtS_spell template:
    &{ template:AtS_spell }{{ title = <spell name> }} {{ splevel = <Spell Level> }} {{ school = <school> }}
    {{ sphere = <sphere (only for priest spells)> }} {{ components = <Components> }} {{ time = <time to cast spell> }}
    {{ range = <Range of spell> }} {{ duration = <How long the effects last> }} {{ aoe = <Area of effect> }}
    {{ save = <saving throw info> }} {{ damage = <amount of damage (optional) > }} {{ damagetype = <Type of Damage (optional) > }}
    {{ healing = <amount of healing (optional) > }} {{ effects = <Description of spell effects> }}
    
Future plans include adding optional fields for the spell template to also handle psionic powers as well, and integrating more complete support for both spells and psionics to use the spell template directly from the character sheet via repeating fieldsets (similar to the 5e sheets)

I am also working on templates for proficiencies, saving throws, ability checks, and rogue skills.
