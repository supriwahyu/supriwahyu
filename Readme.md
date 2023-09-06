 <!DOCTYPE html>
<html>
<head>
<style>
  :root {
  --primary-light: #8abdff;
  --primary: #6d5dfc;
  --primary-dark: #5b0eeb;

  --white: #ffffff;
  --greyLight-1: #e4ebf5;
  --greyLight-2: #c8d0e7;
  --greyLight-3: #bec8e4;
  --greyDark: #9baacf;
}

$shadow: 0.3rem 0.3rem 0.6rem var(--greyLight-2),
  -0.2rem -0.2rem 0.5rem var(--white);
$inner-shadow: inset 0.2rem 0.2rem 0.5rem var(--greyLight-2),
  inset -0.2rem -0.2rem 0.5rem var(--white);

*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: inherit;
}

html {
  box-sizing: border-box;
  font-size: 62.5%; // 1rem = 10px    100% = 16px
  overflow-y: scroll;
  background: var(--greyLight-1);

  @media screen and (min-width: 900px) {
    font-size: 75%;
  }
}

.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: "Poppins", sans-serif;
  background: var(--greyLight-1);
}

.components {
  width: 75rem;
  height: 40rem;
  border-radius: 3rem;
  box-shadow: 0.8rem 0.8rem 1.4rem var(--greyLight-2),
    -0.2rem -0.2rem 1.8rem var(--white);
  padding: 4rem;
  display: grid;
  grid-template-columns: 17.6rem 19rem 20.4rem;
  grid-template-rows: repeat(autofit, min-content);
  grid-column-gap: 5rem;
  grid-row-gap: 2.5rem;
  align-items: center;
}

/*  SWITCH  */
.switch {
  grid-column: 1 / 2;
  display: grid;
  grid-template-columns: repeat(2, min-content);
  grid-gap: 3rem;
  justify-self: center;
  input {
    display: none;
  }

  &__1,
  &__2 {
    width: 6rem;
    label {
      display: flex;
      align-items: center;
      width: 100%;
      height: 3rem;
      box-shadow: $shadow;
      background: rgba(255, 255, 255, 0);
      position: relative;
      cursor: pointer;
      border-radius: 1.6rem;

      &::after {
        content: "";
        position: absolute;
        left: 0.4rem;
        width: 2.1rem;
        height: 2.1rem;
        border-radius: 50%;
        background: var(--greyDark);
        transition: all 0.4s ease;
      }
      &::before {
        content: "";
        width: 100%;
        height: 100%;
        border-radius: inherit;
        background: linear-gradient(
          330deg,
          var(--primary-dark) 0%,
          var(--primary) 50%,
          var(--primary-light) 100%
        );
        opacity: 0;
        transition: all 0.4s ease;
      }
    }
  }
  & input:checked {
    & ~ label {
      &::before {
        opacity: 1;
      }
      &::after {
        left: 57%;
        background: var(--greyLight-1);
      }
    }
  }
}

/*  CHECKBOX  */
.checkbox {
  grid-column: 1 / 2;
  display: grid;
  grid-template-columns: repeat(2, 6rem);
  grid-gap: 3rem;
  justify-content: center;
  input {
    display: none;
  }

  &__1,
  &__2 {
    width: 6rem;
    display: flex;
    justify-content: center;
    label {
      box-shadow: $shadow;
      cursor: pointer;
      position: relative;
      display: flex;
      justify-content: center;
      align-items: center;
      border-radius: 0.5rem;
      width: 2.8rem;
      height: 2.8rem;

      &:hover i {
        color: var(--primary);
      }

      i {
        font-size: 1.8rem;
        font-weight: 700;
        color: var(--greyDark);
        transition: 0.3s ease;
      }
    }

    & input:checked {
      & ~ label {
        box-shadow: $inner-shadow;
        i {
          color: var(--primary);
        }
      }
    }
  }
}

/*  RADIO  */
.radio {
  grid-column: 1 / 2;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  justify-items: center;
  input {
    display: none;
  }

  &__1,
  &__2 {
    & input:checked {
      & ~ label {
        box-shadow: $inner-shadow;
        &::after {
          background: var(--primary);
        }
      }
    }
    label {
      box-shadow: $shadow;
      position: relative;
      display: flex;
      justify-content: center;
      align-items: center;
      cursor: pointer;
      width: 2.8rem;
      height: 2.8rem;
      border-radius: 50%;
      &:hover {
        &::after {
          background: var(--primary);
        }
      }

      &::after {
        content: "";
        position: absolute;
        width: 1.4rem;
        height: 1.4rem;
        background: var(--greyDark);
        border-radius: 50%;
        transition: 0.3s ease;
      }
    }
  }
}

/*  BUTTONS  */
.btn {
  width: 15rem;
  height: 4rem;
  border-radius: 1rem;
  box-shadow: $shadow;
  justify-self: center;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: 0.3s ease;

  &__primary {
    grid-column: 1 / 2;
    grid-row: 4 / 5;
    background: var(--primary);
    box-shadow: inset 0.2rem 0.2rem 1rem var(--primary-light),
      inset -0.2rem -0.2rem 1rem var(--primary-dark), $shadow;
    color: var(--greyLight-1);

    &:hover {
      color: var(--white);
    }
    &:active {
      box-shadow: inset 0.2rem 0.2rem 1rem var(--primary-dark),
        inset -0.2rem -0.2rem 1rem var(--primary-light);
    }
  }

  &__secondary {
    grid-column: 1 / 2;
    grid-row: 5 / 6;
    color: var(--greyDark);
    &:hover {
      color: var(--primary);
    }
    &:active {
      box-shadow: $inner-shadow;
    }
  }

  p {
    font-size: 1.6rem;
  }
}

/*  CLOCK  */
.clock {
  grid-column: 2 / 3;
  grid-row: 1 / 3;
  width: 12rem;
  height: 12rem;
  justify-self: center;
  box-shadow: $shadow;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;

  .hand {
    position: absolute;
    transform-origin: bottom;
    bottom: 6rem;
    border-radius: 0.2rem;
    z-index: 200;
  }

  .hours {
    width: 0.4rem;
    height: 3.2rem;
    background: var(--greyLight-3);
  }

  .minutes {
    width: 0.4rem;
    height: 4.6rem;
    background: var(--greyDark);
  }
  .seconds {
    width: 0.2rem;
    height: 5.2rem;
    background: var(--primary);
  }
  .point {
    position: absolute;
    width: 0.8rem;
    height: 0.8rem;
    border-radius: 50%;
    background: var(--primary);
    z-index: 300;
  }

  .marker {
    width: 95%;
    height: 95%;
    border-radius: 50%;
    position: relative;
    box-shadow: $inner-shadow;

    &::after {
      content: "";
      width: 60%;
      height: 60%;
      position: absolute;
      box-shadow: inset 1px 1px 1px var(--greyLight-2),
        inset -1px -1px 1px var(--white);
      border-radius: 50%;
      top: 20%;
      left: 20%;
      filter: blur(1px);
    }

    &__1,
    &__2,
    &__3,
    &__4 {
      position: absolute;
      border-radius: 0.1rem;
      box-shadow: inset 1px 1px 1px var(--greyLight-2),
        inset -1px -1px 1px var(--white);
    }

    &__1,
    &__2 {
      width: 0.2rem;
      height: 0.6rem;
      left: 5.6rem;
    }

    &__3,
    &__4 {
      width: 0.6rem;
      height: 0.2rem;
      top: 5.6rem;
    }

    &__1 {
      top: 2%;
    }
    &__2 {
      top: 98%;
      transform: translateY(-0.6rem);
    }
    &__3 {
      left: 2%;
    }
    &__4 {
      left: 98%;
      transform: translateX(-0.6rem);
    }
  }
}

/*  CHIP  */
.chip {
  grid-column: 2 / 3;
  grid-row: 3 / 4;
  justify-self: center;
  width: 17rem;
  height: 4rem;
  border-radius: 1rem;
  box-shadow: $shadow;
  display: flex;
  justify-content: space-between;
  align-items: center;

  &__icon {
    width: 3rem;
    height: 3rem;
    border-radius: 1rem;
    margin: 0 0 0 0.2rem;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 1.8rem;
    color: var(--primary);
  }

  p {
    font-size: 0.9rem;
    margin-left: -1.8rem;
    color: var(--greyDark);
  }

  &__close {
    width: 1.6rem;
    height: 1.6rem;
    margin: 0 0.5rem;
    display: flex;
    font-size: 1.6rem;
    color: var(--greyLight-3);
    cursor: pointer;
  }
}

/*  PLAY BUTTON  */
.circle {
  grid-column: 2 / 3;
  grid-row: 4 / 6;
  width: 9rem;
  height: 100%;
  justify-self: center;
  border-radius: 1rem;
  display: grid;
  grid-template-rows: 1fr;
  justify-items: center;
  align-items: center;

  &__btn {
    grid-row: 1 / 2;
    grid-column: 1 / 2;
    width: 6rem;
    height: 6rem;
    display: flex;
    margin: 0.6rem;
    justify-content: center;
    align-items: center;
    border-radius: 50%;
    font-size: 3.2rem;
    color: var(--primary);
    z-index: 300;
    background: var(--greyLight-1);
    box-shadow: $shadow;
    cursor: pointer;
    position: relative;
    &.shadow {
      box-shadow: $inner-shadow;
    }

    .play {
      position: absolute;
      opacity: 0;
      transition: all 0.2s linear;
      &.visibility {
        opacity: 1;
      }
    }
    .pause {
      position: absolute;
      transition: all 0.2s linear;
      &.visibility {
        opacity: 0;
      }
    }
  }

  &__back-1,
  &__back-2 {
    grid-row: 1 / 2;
    grid-column: 1 / 2;
    width: 6rem;
    height: 6rem;
    border-radius: 50%;
    filter: blur(1px);
    z-index: 100;
  }

  &__back-1 {
    box-shadow: 0.4rem 0.4rem 0.8rem var(--greyLight-2),
      -0.4rem -0.4rem 0.8rem var(--white);
    background: linear-gradient(
      to bottom right,
      var(--greyLight-2) 0%,
      var(--white) 100%
    );
    animation: waves 4s linear infinite;

    &.paused {
      animation-play-state: paused;
    }
  }

  &__back-2 {
    box-shadow: 0.4rem 0.4rem 0.8rem var(--greyLight-2),
      -0.4rem -0.4rem 0.8rem var(--white);
    animation: waves 4s linear 2s infinite;

    &.paused {
      animation-play-state: paused;
    }
  }
}

/*  FORM  */
.form {
  grid-column: 3 / 4;
  grid-row: 3 / 4;

  &__input {
    width: 20.4rem;
    height: 4rem;
    border: none;
    border-radius: 1rem;
    font-size: 1.4rem;
    padding-left: 1.4rem;
    box-shadow: $inner-shadow;
    background: none;
    font-family: inherit;
    color: var(--greyDark);

    &::placeholder {
      color: var(--greyLight-3);
    }
    &:focus {
      outline: none;
      box-shadow: $shadow;
    }
  }
}

/*  SEARCH  */
.search {
  grid-column: 3 / 4;
  grid-row: 2 / 3;
  position: relative;
  display: flex;
  align-items: center;

  &__input {
    width: 20.4rem;
    height: 4rem;
    border: none;
    border-radius: 1rem;
    font-size: 1.4rem;
    padding-left: 3.8rem;
    box-shadow: $inner-shadow;
    background: none;
    font-family: inherit;
    color: var(--greyDark);

    &::placeholder {
      color: var(--greyLight-3);
    }
    &:focus {
      outline: none;
      box-shadow: $shadow;

      + .search__icon {
        color: var(--primary);
      }
    }
  }

  &__icon {
    height: 2rem;
    position: absolute;
    font-size: 2rem;
    padding: 0 1rem;
    display: flex;
    color: var(--greyDark);
    transition: 0.3s ease;
  }
}

/*  SEGMENTED-CONTROL */
.segmented-control {
  grid-column: 3 / 4;
  grid-row: 1 / 2;
  width: 20.4rem;
  height: 4rem;
  box-shadow: $shadow;
  border-radius: 1rem;
  display: flex;
  align-items: center;
  position: relative;

  input {
    display: none;
  }

  > input:checked + label {
    transition: all 0.5s ease;
    color: var(--primary);
  }

  &__1,
  &__2,
  &__3 {
    width: 6.8rem;
    height: 3.6rem;
    font-size: 1.4rem;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    color: var(--greyDark);
    transition: all 0.5s ease;

    &:hover {
      color: var(--primary);
    }
  }

  &__color {
    position: absolute;
    height: 3.4rem;
    width: 6.2rem;
    margin-left: 0.3rem;
    border-radius: 0.8rem;
    box-shadow: $inner-shadow;
    pointer-events: none;
  }
}

#tab-1:checked ~ .segmented-control__color {
  transform: translateX(0);
  transition: transform 0.3s cubic-bezier(0.645, 0.045, 0.355, 1);
}
#tab-2:checked ~ .segmented-control__color {
  transform: translateX(6.8rem);
  transition: transform 0.3s cubic-bezier(0.645, 0.045, 0.355, 1);
}
#tab-3:checked ~ .segmented-control__color {
  transform: translateX(13.6rem);
  transition: transform 0.3s cubic-bezier(0.645, 0.045, 0.355, 1);
}

/*  ICONS  */
.icon {
  grid-column: 3 / 4;
  grid-row: 4 / 5;
  display: flex;
  justify-content: space-between;
  &__account,
  &__home,
  &__settings {
    width: 4rem;
    height: 4rem;
    border-radius: 50%;
    box-shadow: $shadow;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 2rem;
    cursor: pointer;
    color: var(--greyDark);
    transition: all 0.5s ease;

    &:active {
      box-shadow: $inner-shadow;
      color: var(--primary);
    }
    &:hover {
      color: var(--primary);
    }
  }
}

/*  RANGE-SLIDER  */
.slider {
  grid-column: 3 / 4;
  grid-row: 5 / 6;
  align-self: center;
  display: flex;
  flex-direction: column;

  &__box {
    width: 100%;
    height: 1rem;
    cursor: pointer;
    box-shadow: $inner-shadow;
    border-radius: 1rem;
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  &__btn {
    width: 2rem;
    height: 2rem;
    border-radius: 50%;
    background: var(--white);
    position: absolute;
    box-shadow: 0px 0.1rem 0.3rem 0px var(--greyLight-3);
    z-index: 200;
    display: flex;
    justify-content: center;
    align-items: center;

    &:hover ~ .slider__tooltip {
      opacity: 1;
    }
    &::after {
      content: "";
      position: absolute;
      width: 0.8rem;
      height: 0.8rem;
      border-radius: 50%;
      box-shadow: $inner-shadow;
    }
  }

  &__color {
    height: 100%;
    width: 50%;
    position: absolute;
    left: 0;
    z-index: 100;
    border-radius: inherit;
    background: var(--primary);
    background: linear-gradient(
      -1deg,
      var(--primary-dark) 0%,
      var(--primary) 50%,
      var(--primary-light) 100%
    );
  }

  &__tooltip {
    position: absolute;
    top: 2.6rem;
    height: 2.5rem;
    width: 3rem;
    border-radius: 0.6rem;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 1.2rem;
    color: var(--primary);
    box-shadow: $shadow;
    opacity: 0;
    transition: opacity 0.3s ease;
  }
}

@keyframes waves {
  0% {
    transform: scale(1);
    opacity: 1;
  }

  50% {
    opacity: 1;
  }

  100% {
    transform: scale(2);
    opacity: 0;
  }
}

.dribbble {
  position: fixed;
  font-size: 2.6rem;
  right: 2rem;
  bottom: 1rem;
  color: #ea4c89;
}

</style>
</head>

<body>
<div class="clock">
      <div class="hand hours"></div>
      <div class="hand minutes"></div>
      <div class="hand seconds"></div>
      <div class="point"></div>
      <div class="marker">
        <span class="marker__1"></span>
        <span class="marker__2"></span>
        <span class="marker__3"></span>
        <span class="marker__4"></span>
      </div>
    </div>
</body>
<script>
  /*  clock */
const hours = document.querySelector('.hours');
const minutes = document.querySelector('.minutes');
const seconds = document.querySelector('.seconds');

/*  play button */
const play = document.querySelector('.play');
const pause = document.querySelector('.pause');
const playBtn = document.querySelector('.circle__btn');
const wave1 = document.querySelector('.circle__back-1');
const wave2 = document.querySelector('.circle__back-2');

/*  rate slider */
const container = document.querySelector('.slider__box');
const btn = document.querySelector('.slider__btn');
const color = document.querySelector('.slider__color');
const tooltip = document.querySelector('.slider__tooltip');

clock = () => {
  let today = new Date();
  let h = (today.getHours() % 12) + today.getMinutes() / 59; // 22 % 12 = 10pm
  let m = today.getMinutes(); // 0 - 59
  let s = today.getSeconds(); // 0 - 59

  h *= 30; // 12 * 30 = 360deg
  m *= 6;
  s *= 6; // 60 * 6 = 360deg

  rotation(hours, h);
  rotation(minutes, m);
  rotation(seconds, s);

  // call every second
  setTimeout(clock, 500);
}

rotation = (target, val) => {
  target.style.transform =  `rotate(${val}deg)`;
}

window.onload = clock();

dragElement = (target, btn) => {
  target.addEventListener('mousedown', (e) => {
      onMouseMove(e);
      window.addEventListener('mousemove', onMouseMove);
      window.addEventListener('mouseup', onMouseUp);
  });

  onMouseMove = (e) => {
      e.preventDefault();
      let targetRect = target.getBoundingClientRect();
      let x = e.pageX - targetRect.left + 10;
      if (x > targetRect.width) { x = targetRect.width};
      if (x < 0){ x = 0};
      btn.x = x - 10;
      btn.style.left = btn.x + 'px';

      // get the position of the button inside the container (%)
      let percentPosition = (btn.x + 10) / targetRect.width * 100;
      
      // color width = position of button (%)
      color.style.width = percentPosition + "%";

      // move the tooltip when button moves, and show the tooltip
      tooltip.style.left = btn.x - 5 + 'px';
      tooltip.style.opacity = 1;

      // show the percentage in the tooltip
      tooltip.textContent = Math.round(percentPosition) + '%';
  };

  onMouseUp  = (e) => {
      window.removeEventListener('mousemove', onMouseMove);
      tooltip.style.opacity = 0;

      btn.addEventListener('mouseover', function() {
        tooltip.style.opacity = 1;
      });
      
      btn.addEventListener('mouseout', function() {
        tooltip.style.opacity = 0;
      });
  };
};

dragElement(container, btn);

/*  play button  */
playBtn.addEventListener('click', function(e) {
  e.preventDefault();
  pause.classList.toggle('visibility');
  play.classList.toggle('visibility');
  playBtn.classList.toggle('shadow');
  wave1.classList.toggle('paused');
  wave2.classList.toggle('paused');
});
</script>
</html> 
