# Options

[English](CONFIGURATION.md), [한국어](CONFIGURATION.ko.md)

Default config file is located at `/etc/xdg/kime/config.yaml`. Check
[default_config.yaml](../res/default_config.yaml) to see the default configuration
file. You edit `/etc/xdg/kime/config.yaml` or create a new config file at
`~/.config/kime/config.yaml`.

You can also change the location of config file using [`$XDG_CONFIG_DIR` or
`$XDG_CONFIG_HOME`][xdg] environment variable. kime will try to read
`$XDG_CONFIG_DIR/kime/config.yaml` and `$XDG_CONFIG_HOME/kime/config.yaml` too.

[xdg]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html#introduction

## layout

Hangul layout name. "dubeolsik", "sebeolsik-390", and "sebeolsik-391" are
available as default. Custom layout can be added by creating layout YAML files
at `$XDG_CONFIG_HOME/kime/layouts/` directory. See [dubeolsik.yaml] for the
structure of keyboard layout file.

[dubeolsik.yaml]: ../src/engine/core/data/dubeolsik.yaml

| default |`dubeolsik`|
|---------|-----------|

## global_hangul_state

Set hangul state globally

| default |`false`|
|---------|-------|

## word_commit

Let commit by word

| default |`false`|
|---------|-------|

## hotkeys

Set engine hotkey format is `Key: Content`

### content

#### behavior

##### ToggleHangul

Toggle hangul mode

##### ToEnglish

Set english mode

##### ToHangul

Set hangul mode

##### Commit

End current preedit state then commit

#### result

##### Bypass

Bypass key to continue key process

##### Consume

Consume key to end key process

##### ConsumeIfProcessed

When hotkey processed it act like Consume otherwise it act like Bypass

### default

```yaml
Esc:
  behavior: ToEnglish
  result: Bypass
AltR:
  behavior: ToggleHangul
  result: Consume
Muhenkan:
  behavior: ToggleHangul
  result: Consume
Hangul:
  behavior: ToggleHangul
  result: Consume
Super-Space:
  behavior: ToggleHangul
  result: Consume
```

## xim_preedit_font

Preedit window font name and size for XIM

| default |`[D2Coding, 15.0]`|
|---------|------------------|

## layout_addons

Adjust layout addons

format is `layout_name: [Addon]`, `all` applys all layouts

### default

```yaml
all:
  - ComposeChoseongSsang
dubeolsik:
  - TreatJongseongAsChoseongg
```

### Addons

#### TreatJongseongAsChoseong

Treat jongseong as choseong

```txt
간 + ㅏ = 가나
값 + ㅏ = 갑사
```

#### FlexibleComposeOrder

Compose choseong and jungseong even order is reversed it could be help for fix typo error.

```txt
ㅏ + ㄱ = 가
ㅚ + ㄱ = 괴
```

#### ComposeChoseongSsang

When you press same choseong it will be ssangjaum

```txt
ㄱ + ㄱ = ㄲ
ㅅ + ㅅ = ㅆ
ㄷ + ㄷ = ㄸ
ㅂ + ㅂ = ㅃ
ㅈ + ㅈ = ㅉ
```

#### DecomposeChoseongSsang

Same as above but work on backspace(e.g. ㄲ -> ㄱ)

#### ComposeJungseongSsang

```txt
ㅑ + ㅣ = ㅒ
ㅕ + ㅣ = ㅖ
```

#### DecomposeJungseongSsang

#### ComposeJongseongSsang

```txt
ㄱ + ㄱ = ㄲ
ㅅ + ㅅ = ㅆ
```

#### DecomposeJongseongSsang
