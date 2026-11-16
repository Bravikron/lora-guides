# How to pick images for a character LoRA

*Bravikron Labs · Free guide · Updated 6 November 2026*

The dataset decides almost everything. This short guide covers how many images you need, which ones to keep, which ones to throw away, and how to caption them.

Works for Qwen-Image, Flux, SDXL and most modern models. A printable version with a checklist is in [`Bravikron_LoRA_Image_Guide.pdf`](Bravikron_LoRA_Image_Guide.pdf). Web version: <https://bravikron.com/lora-image-guide.html>

## 01 · Why it matters: your LoRA learns your mistakes too

A LoRA copies whatever your images have in common. If most of your images are close-ups in warm light, it learns "this character is always a warm close-up." If the face slowly drifts across your images, it learns the drifted face. Training settings can't fix a bad dataset, but a good dataset works with almost any sensible settings.

> **Real example.** One of our character LoRAs kept producing a narrower jaw and darker skin than the reference. The cause wasn't the settings. Half the training images had small faces (under 200 pixels) and the face had drifted in those. We remade the dataset with mostly close-ups and the problem was gone.

## 02 · How many: fewer, better images

| Images | |
|---|---|
| **15** | The minimum for a usable character |
| **20–25** | The sweet spot for most characters |
| **40** | Rarely needed. More images add more chances for drift. |

Twenty strong, varied images beat sixty similar ones. When you're unsure about an image, leave it out.

## 03 · The mix: mostly close, some far

The face and the small details are the hardest part, so they get the most images. Full-body shots teach proportions and outfit.

- **40%** close-ups
- **35%** head-and-shoulders or half body
- **25%** full body

For 24 images, that's about 10 close-ups, 8 head-and-shoulders or half-body shots, and 6 full-body shots.

## 04 · Variety: change everything except the character

The character should be the only thing every image has in common. Change everything around it.

| | |
|---|---|
| **Angle** | Front, three-quarter left and right, side profile, back view, from slightly above and below |
| **Expression** | Neutral, smiling, laughing, angry, sad, surprised, thinking |
| **Lighting** | Soft daylight, warm lamp, cool night light, dramatic side light |
| **Background** | Plain, indoors, outdoors, busy, simple. Avoid the same wall in every shot. |
| **Pose** | Standing, sitting, walking, pointing, holding objects |
| **Outfit** | The signature outfit in most images, plus 2–4 others so the outfit can be changed later |

## 05 · Consistency: write down the must-keep details

Before you collect anything, list the 3–6 details that make the character recognizable, such as eye colour, a scar, a hair shape, an ear notch or a tail tip. Then check every image against that list.

> **Small marks drift first.** Moles, scars and notches tend to move to the other side, change size or disappear. Check them in every single image. One image with the scar on the wrong cheek is enough to confuse the LoRA.

## 06 · Keep or cut: the keep-or-cut test

**Keep**

- Sharp, well lit and clearly the character
- The face is big enough to see the details (200+ pixels across)
- Every must-keep detail is correct
- It adds an angle, expression or setting you don't have yet
- At least 1024 pixels on the short side when possible

**Cut**

- Blurry, heavily compressed or tiny
- The face is cut off by the frame or hidden
- Other characters prominent in the shot
- Text, logos, watermarks or signatures
- Heavy filters or a very different art style
- A near-copy of an image you already kept
- Any must-keep detail is wrong

## 07 · Captions: caption what changes, not what stays

Start every caption with a rare trigger word, then describe only the things that change between images: the shot, the pose, the expression, the setting and the outfit. Leave the fixed features out. The LoRA then links them to the trigger word, so you never have to describe them again.

Good:

```
mychar, close-up portrait, three-quarter view, laughing, warm lamp light, cozy kitchen, wearing a green sweater
```

Bad (the part in brackets describes fixed features):

```
mychar, [a girl with green eyes and a scar on her left cheek and red curly hair,] close-up portrait ...
```

Pick a rare trigger and test it. A common word like "Anna" pulls results toward its usual meaning. On Z-Image, wr3nn sometimes printed as text on clothes, so we test full names too. More on that in [the trigger-word guide](trigger-word-text-on-clothes.md).

## 08 · Rights: only train on images you're allowed to use

- Your own art, your own generations, or images you have written permission to use.
- Never a real person without their clear consent.
- No characters owned by studios or brands if you plan to share or sell the LoRA.
- Check that your base model's licence allows what you plan to do with the LoRA.

## Checklist: before you press Train

- [ ] 15–40 images, ideally 20–25
- [ ] About 40% close-ups, 35% mid shots, 25% full body
- [ ] At least 5 different angles
- [ ] At least 5 different expressions
- [ ] Several lighting setups and backgrounds
- [ ] Must-keep details checked in every image
- [ ] No blur, text, watermarks or other characters
- [ ] Faces at least 200 pixels across
- [ ] Every caption starts with the trigger word
- [ ] Captions describe only what changes
- [ ] You have the rights to every image
- [ ] The base model licence fits your plans

---

Don't want to do all of this yourself? Bravikron Labs trains custom character and style LoRAs: <https://bravikron.com/labs.html>
