<script lang="ts">
    const LAMP = {
        entity_id: "light.0x7cb03eaa0a03e828",
        state: "on",
        attributes: {
            effect_list: [
                "blink",
                "breathe",
                "okay",
                "channel_change",
                "finish_effect",
                "stop_effect",
            ],
            brightness: 23,
            linkquality: 110,
            state: "ON",
            update: {
                state: "available",
            },
            update_available: true,
            friendly_name: "0x7cb03eaa0a03e828",
            supported_features: 45,
        },
        last_changed: "2020-12-17T14:09:40.148957+00:00",
        last_updated: "2020-12-17T14:09:40.148957+00:00",
        context: {
            id: "29a23755fd4524ce1c7c27f6274dd383",
            parent_id: null,
            user_id: null,
        },
    };
    const name = LAMP.entity_id.split(".")[0];
    let isOn = LAMP.state === "on";
    $: src_lamp = isOn
        ? "https://previews.123rf.com/images/dvarg/dvarg1203/dvarg120300019/12676347-light-filament-lamp-on-a-white-background-illustration-for-design.jpg"
        : "https://previews.123rf.com/images/pixelrobot/pixelrobot1504/pixelrobot150400921/38251282-100-watt-light-bulb-off-isolated-on-white-background-.jpg";

    let br = LAMP.attributes.brightness;

    function switch_lamp() {
        const body = JSON.stringify(
            isOn
                ? {
                      domain: "light",
                      service: "turn_off",
                  }
                : {
                      domain: "light",
                      service: "turn_on",
                      service_data: {
                          brightness_pct: 25,
                      },
                  }
        );
        const headers = new Headers();
        headers.set("Content-Type", "application/json");

        fetch(`http://localhost:3000/entity/state/${LAMP.entity_id}`, {
            headers,
            method: "PUT",
            body: body,
        })
            .then((x) => x.text())
            .then(console.log)
            .catch(console.log);
        isOn = !isOn;
    }

    function change() {
        const body = JSON.stringify({
            domain: "light",
            service: "turn_on",
            service_data: {
                brightness_pct: br,
            },
        });
        const headers = new Headers();
        headers.set("Content-Type", "application/json");
        fetch(`http://localhost:3000/entity/state/${LAMP.entity_id}`, {
            headers,
            method: "PUT",
            body: body,
        });
    }
</script>

<style>
</style>

<template>
    <h1>Lamp: {name} is {isOn ? 'on' : 'off'}</h1>
    <img
        src={src_lamp}
        width="100px"
        height="100px"
        alt=""
        on:click={switch_lamp} />
    {#if isOn}<input type="range" bind:value={br} on:change={change} />{/if}
    ({br})
</template>
