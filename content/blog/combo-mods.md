---
title: 'Combo Mods: A less error-prone alternative to home-row mods'
date: 2022-02-16
summary: It didn't take long after getting my Keyboardio Atreus for me to try out home-row mods. I used them for several months and really wanted to like them -- it's so convenient to have all your modifiers on the home row -- but I could never get the timing configuration right. In their place, I discovered combo mods, which are almost as convenient and much less error-prone.
---

It didn't take long after getting my [Keyboardio Atreus](/blog/atreus-review) for me to try out [home-row mods](https://precondition.github.io/home-row-mods). I used them for several months and really wanted to like them -- it's so convenient to have all your modifiers on the home row -- but I could never get the timing configuration right. I was triggering modifiers while typing quickly (or typing characters when I wanted to trigger modifiers) often enough that I eventually gave up on home-row mods. In their place, I discovered combo mods, which are almost as convenient and much less error-prone, at least for me.

In keyboard-nerd-speak, combos are a way to use chording -- pressing multiple keys at the same time -- to trigger a keypress. They're a great way to do more with a tiny keyboard, and I find that it's easier to avoid accidental triggers with combos than with mod-tap keys (keys that do one thing when tapped quickly and another when held down, such as home-row mods). Combos aren't perfect, but with modifiers, which are always held down, you can make the keyboard a bit smarter about when it triggers the combos -- more on that later.

In my current setup, I have `ctrl`, `super` (or `cmd` or `meta` or whatever), and `alt`, as well as any combination of them, available on both my left and right hand using combos:

- `F` + `D` = `ctrl`
- `F` + `S` = `super`
- `F` + `A` = `alt`
- `F` + `D` + `S` = `ctrl` + `super`
- and so on...

{{% aside %}}
This post lists keys from the QWERTY layout since that's what most people use. I actually type with the [Colemak](https://colemak.com/) layout, though.
{{% /aside %}}

Notably, I don't have `shift` as a combo mod, partly because it's so frequently used that it deserves a dedicated key and partly because with four home row keys per hand, only three modifiers (and the combinations of them) really fit on each. `shift` lives on one of my keyboard's thumb keys instead.

The key to making combo mods work well is to configure them such that all keys in the combo must be pressed in very quick succession (mine are set to 25 milliseconds currently) *and* at least one of the keys must be held longer than a typical keypress (175 milliseconds for me currently). By setting both of these constraints, it becomes very difficult to accidentally trigger the combo in normal typing.

The [QMK firmware](https://qmk.fm/), which is what my Atreus runs, makes it easy to set up mod combos as I've described them. Here's how I set them up currently, with explanatory comments added:

```c
// config.h

#define COMBO_TERM 25        // how quickly all combo keys must be pressed in succession to trigger
#define COMBO_MUST_HOLD_MODS // if a combo triggers a modifier, only trigger when the combo is held
#define COMBO_HOLD_TERM 175  // how long at least one of the combo keys must be held to trigger
```

```c
// keymap.c

// define combo names
enum combos {
    COMBO_LCTL,
    COMBO_LGUI,
    COMBO_LALT,
    COMBO_LCTLGUI,
    // more here...

    COMBO_LENGTH // nifty trick to avoid manually specifying how many combos you have
};

uint16_t COMBO_LEN = COMBO_LENGTH; // nifty trick continued

// define keys that make up combos
const uint16_t PROGMEM fd_combo[] = {KC_F, KC_D, COMBO_END};
const uint16_t PROGMEM fs_combo[] = {KC_F, KC_S, COMBO_END};
const uint16_t PROGMEM fa_combo[] = {KC_F, KC_A, COMBO_END};
const uint16_t PROGMEM fds_combo[] = {KC_F, KC_D, KC_S, COMBO_END};
// more here...

// map combo names to their keys and the key they trigger
combo_t key_combos[] = {
    [COMBO_LCTL] = COMBO(fd_combo, KC_LCTL),
    [COMBO_LGUI] = COMBO(fs_combo, KC_LGUI),
    [COMBO_LALT] = COMBO(fa_combo, KC_LALT),
    [COMBO_LCTLGUI] = COMBO(fds_combo, LCTL(KC_LGUI)),
    // more here...
};
```

{{% aside %}}
You can check out the [QMK combo docs](https://docs.qmk.fm/#/feature_combo) to learn more about how combos work and the cool things you can do with them.
{{% /aside %}}

I've been using combo mods for over four months now, and I'm quite happy with the setup. I can't remember the last time I accidentally triggered a modifier when I wanted to type letters instead. I haven't seen much discussion of combo mods (at least not on the home row like this) among other tiny keyboard users online, and I hope this post will spread the idea to a few more people.
