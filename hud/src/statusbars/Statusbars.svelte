<script>
    let healthWidth = `width: 0%`;
    let foodWidth = `width: 100%`;
    let xpWidth = `width: 0%`;

    function handlePlayerHealthChange(event) {
        const percentage = ((event.getHealth() / event.getMaxHealth()) * 100);
        healthWidth = 'width: ' + percentage + "%";
    }

    function handlePlayerFoodLevelChange(event) {
        const percentage = ((event.getFoodLevel() / 20) * 100);
        foodWidth = 'width: ' + percentage + "%";
    }

    function handlePlayerExperienceProgressChange(event) {
        const percentage = (event.getExperienceProgress() * 100);
        xpWidth = 'width: ' + percentage + "%";
    }

    try {
        events.on("playerHealthChange", handlePlayerHealthChange);
        events.on("playerFoodLevelChange", handlePlayerFoodLevelChange);
        events.on("playerExperienceProgressChange", handlePlayerExperienceProgressChange)
    } catch(err) {
        console.log(err);
    }
</script>

<div class="statusbars">
    <div class="top">
        <div class="health-bar">
            <div style={healthWidth} class="current"></div>
        </div>
        <div class="food-bar">
            <div style={foodWidth} class="current"></div>
        </div>
    </div>
    <div class="experience-bar">
        <div style={xpWidth} class="current"></div>
    </div>
</div>

<style lang="scss">
  .statusbars {
    position: absolute;
    bottom: 58px;
    left: 50%;
    transform: translateX(-50%);
    width: 378px;
  }

  .top {
    display: flex;
    margin-bottom: 8px;
  }

  .health-bar {
    width: 179px;
    height: 16px;
    background: rgba(0, 0, 0, 0.5);
    border-radius: 8px;
    overflow: hidden;
    margin-right: 20px;

    .current {
      background: #FC4130;
    }
  }

  .food-bar {
    width: 179px;
    height: 16px;
    background: rgba(0, 0, 0, 0.5);
    border-radius: 8px;
    overflow: hidden;

    .current {
      background: #B88458;
    }
  }

  .experience-bar {
    width: 100%;
    height: 16px;
    background: rgba(0, 0, 0, 0.5);
    border-radius: 8px;
    overflow: hidden;

    .current {
      background: #88C657;
    }
  }

  .current {
    height: 100%;
    transition: ease width .2s;
  }
</style>
