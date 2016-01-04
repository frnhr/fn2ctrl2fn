# fn2ctrl2fn
Karabiner config for replacing FN and Left CTRL keys.

## What?

I'm tired of having to think about where my left Ctrl key is! Because on Apple wired keyboard, it is the leftmost key, but on integrated keyboard on my Macbook Pro, that is the FN key (and left ctrl is just next to it).

### But really, why??

his causes me to make a lot of errors when using F1-12 keys. I use F7 and F8 keys very often, and it is very annoying when instead of the desired effect (debugger stepping though code) my laptop starts playing music! NO MORE!!!!!one

## Ok, how?

There is this nice tool called [Karabiner](https://pqrs.org/osx/karabiner/). It can really remap keys, not just sorta-all-of-them-mostly.

### Ok, so what's in this repo, if there is this app that does the job?

Well, in order to configure Karabiner, one must write the config in XML. Yeah... 

So here it is, XML config that replaces `FN` and `LEFT_CTRL` keys:

```
<?xml version="1.0"?>
<root>
  <item>
    <name>Swap FN and Ctrl on Integrated keyboard</name>
    <identifier>private.integrated_swap_fn_and_ctrl</identifier>
    <!-- Apple Internal Keyboard / Trackpad (Apple Inc.) --><!-- Device ID is VERIFIED! -->
    <device_only>DeviceVendor::RawValue::0x05ac,DeviceProduct::RawValue::0x0253</device_only>

    <!--     Remap LEFT_CTRL => FN     -->
    <autogen>
      __KeyToKey__ KeyCode::CONTROL_L, 
                   KeyCode::FN
    </autogen>
    <!-- FN keeys need to be remapped explicitly, because Karabiner gets different codes for them -->
    <autogen> __KeyToKey__  ConsumerKeyCode::BRIGHTNESS_DOWN, ModifierFlag::FN, 
                            KeyCode::F1  </autogen>
    <autogen> __KeyToKey__  ConsumerKeyCode::BRIGHTNESS_UP, ModifierFlag::FN,
                            KeyCode::F2  </autogen>
    <autogen> __KeyToKey__  KeyCode::MISSION_CONTROL, ModifierFlag::FN,
                            KeyCode::F3  </autogen>
    <autogen> __DropKeyAfterRemap__ KeyCode::MISSION_CONTROL, ModifierFlag::FN </autogen>
    <autogen> __KeyToKey__  KeyCode::LAUNCHPAD, ModifierFlag::FN,
                            KeyCode::F4  </autogen>
    <autogen> __DropKeyAfterRemap__ KeyCode::LAUNCHPAD, ModifierFlag::FN </autogen>
    <autogen> __KeyToKey__  ConsumerKeyCode::KEYBOARDLIGHT_LOW, ModifierFlag::FN,
                            KeyCode::F5  </autogen>
    <autogen> __KeyToKey__  ConsumerKeyCode::KEYBOARDLIGHT_HIGH, ModifierFlag::FN,
                            KeyCode::F6  </autogen>
    <autogen> __KeyToKey__  ConsumerKeyCode::MUSIC_PREV, ModifierFlag::FN,
                            KeyCode::F7  </autogen>
    <autogen> __KeyToKey__  ConsumerKeyCode::MUSIC_PLAY, ModifierFlag::FN,
                            KeyCode::F8  </autogen>
    <autogen> __KeyToKey__  ConsumerKeyCode::MUSIC_NEXT, ModifierFlag::FN,
                            KeyCode::F9  </autogen>
    <autogen> __KeyToKey__  ConsumerKeyCode::VOLUME_MUTE, ModifierFlag::FN,
                            KeyCode::F10  </autogen>
    <autogen> __KeyToKey__  ConsumerKeyCode::VOLUME_DOWN, ModifierFlag::FN,
                            KeyCode::F11  </autogen>
    <autogen> __KeyToKey__  ConsumerKeyCode::VOLUME_UP, ModifierFlag::FN,
                            KeyCode::F12  </autogen>


    <!--     Remap FN => LEFT_CTRL     -->
    <autogen>
      __KeyToKey__ KeyCode::FN, 
                   KeyCode::CONTROL_L
    </autogen>                            
    <!-- FN keeys need to be remapped explicitly, because Karabiner gets different codes for them -->
    <autogen> __KeyToKey__  KeyCode::F1, ModifierFlag::CONTROL_L,
                            ConsumerKeyCode::BRIGHTNESS_DOWN, ModifierFlag::CONTROL_L  </autogen>
    <autogen> __KeyToKey__  KeyCode::F2, ModifierFlag::CONTROL_L,
                            ConsumerKeyCode::BRIGHTNESS_UP, ModifierFlag::CONTROL_L  </autogen>
    <autogen> __KeyToKey__  KeyCode::F3, ModifierFlag::CONTROL_L,
                            KeyCode::MISSION_CONTROL, ModifierFlag::CONTROL_L  </autogen>
    <autogen> __KeyToKey__  KeyCode::F4, ModifierFlag::CONTROL_L,
                            KeyCode::LAUNCHPAD, ModifierFlag::CONTROL_L  </autogen>
    <autogen> __KeyToKey__  KeyCode::F5, ModifierFlag::CONTROL_L,
                            ConsumerKeyCode::KEYBOARDLIGHT_LOW, ModifierFlag::CONTROL_L  </autogen>
    <autogen> __KeyToKey__  KeyCode::F6, ModifierFlag::CONTROL_L,
                            ConsumerKeyCode::KEYBOARDLIGHT_HIGH, ModifierFlag::CONTROL_L  </autogen>
    <autogen> __KeyToKey__  KeyCode::F7, ModifierFlag::CONTROL_L,
                            ConsumerKeyCode::MUSIC_PREV, ModifierFlag::CONTROL_L  </autogen>
    <autogen> __KeyToKey__  KeyCode::F8, ModifierFlag::CONTROL_L,
                            ConsumerKeyCode::MUSIC_PLAY, ModifierFlag::CONTROL_L  </autogen>
    <autogen> __KeyToKey__  KeyCode::F9, ModifierFlag::CONTROL_L,
                            ConsumerKeyCode::MUSIC_NEXT, ModifierFlag::CONTROL_L  </autogen>
    <autogen> __KeyToKey__  KeyCode::F10, ModifierFlag::CONTROL_L,
                            ConsumerKeyCode::VOLUME_MUTE, ModifierFlag::CONTROL_L  </autogen>
    <autogen> __KeyToKey__  KeyCode::F11, ModifierFlag::CONTROL_L,
                            ConsumerKeyCode::VOLUME_DOWN, ModifierFlag::CONTROL_L  </autogen>
    <autogen> __KeyToKey__  KeyCode::F12, ModifierFlag::CONTROL_L,
                            ConsumerKeyCode::VOLUME_UP, ModifierFlag::CONTROL_L  </autogen>

  </item>
</root>
```

## But wait! If I use this, then my keys will be swapped, and it will be confusing...

Yes. You can physically replace those keys, though :)

![alt text](https://raw.githubusercontent.com/frnhr/fn2ctrl2fn/master/swapped_keys.jpg "Swapped FN and LEFT_CTRL keys")


## Caveats

##### Only works while Karabiner is running

Meaning it won't work while you are:
 * reinstalling OSX,
 * booting that system restore thing,
 * using BootCamp (I guess),
 * at the login screen,
 * etc.


##### Apple changes those FN keys over fairly often over the years

So you might need to update the codes for your function keys, depending on your exact keyboard (e.g. "Mission control" vs "Expose").
In this case, refer to these lists:
https://github.com/tekezo/Karabiner/blob/master/src/bridge/generator/keycode/data/ConsumerKeyCode.data
https://github.com/tekezo/Karabiner/blob/master/src/bridge/generator/keycode/data/KeyCode.data



