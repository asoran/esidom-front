<script lang="typescript">
    const sensor = { 
        entity_id: "sensor.fibaro_system_fgms001_zw5_motion_sensor_temperature",
        state: "unavailable",
        attributes: {
            restored: true,
            supported_features: 0,
            unit_of_measurement: "°C",
            friendly_name: "FIBARO System FGMS001-ZW5 Motion Sensor Temperature"
        },
        last_changed: "2020-12-17T14:09:07.024845+00:00",
        last_updated: "2020-12-17T14:09:07.024845+00:00",
            context: {
                id: "1c6e66796797066c8ae65da9c0ab3653",
                parent_id: null,
                user_id: null
            },
        };

    const name = sensor.attributes.friendly_name;
    const state = sensor.state;

</script>

<template>
    <div class=" flex bg-indigo-100 rounded-xl w-max min-w-full md:min-w-0">
        <div class="flex-none w-20 relative mt-2">
            <img class = "object-contain md:object-scale-down"
            src= https://denkavit.com/fr/wp-content/uploads/sites/11/2017/07/Temperature.png 
            alt=""
            />
        </div>
        <form class="flex-auto p-6">
            <div class="flex flex-wrap">
                <h1 class="flex-auto text-base font-semibold">
                    {name}
                </h1>
            </div>
            <div class="w-full flex-none text-xs font-medium text-gray-500 mt-1">
                {state}
            </div>
        </form>
    </div>
</template>
