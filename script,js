document.addEventListener('DOMContentLoaded', () => {
  const stepHint = document.getElementById('stepHint');
  const bottleStage = document.getElementById('bottleStage');
  const corkBtn = document.getElementById('corkBtn');
  const corkRing = document.getElementById('corkRing');
  const glassBottle = document.getElementById('glassBottle');
  const scrollRoll = document.getElementById('scrollRoll');
  const scrollCard = document.getElementById('scrollCard');
  const resetBtn = document.getElementById('resetBtn');
  const bubblesLayer = document.getElementById('bubblesLayer');

  let state = 'sealed';

  function createAmbientBubbles() {
    const bubbleCount = 12;
    for (let i = 0; i < bubbleCount; i++) {
      const bubble = document.createElement('span');
      bubble.className = 'bubble';

      const size = 8 + Math.random() * 14;
      bubble.style.width = `${size}px`;
      bubble.style.height = `${size}px`;
      bubble.style.left = `${5 + Math.random() * 90}%`;
      bubble.style.animationDuration = `${11 + Math.random() * 10}s`;
      bubble.style.animationDelay = `${Math.random() * 10}s`;

      bubblesLayer.appendChild(bubble);
    }
  }

  function handleUncork(e) {
    if (e) e.stopPropagation();
    if (state !== 'sealed') return;

    state = 'uncorked';
    corkBtn.classList.add('popped');
    corkRing.style.display = 'none';

    glassBottle.classList.add('is-interactive');
    glassBottle.setAttribute('tabindex', '0');

    stepHint.textContent = 'Tap the bottle to pull out the scroll';
  }

  function handlePullScroll() {
    if (state !== 'uncorked') return;

    state = 'opened';
    glassBottle.classList.remove('is-interactive');
    glassBottle.setAttribute('tabindex', '-1');

    scrollRoll.classList.add('pop-out');
    stepHint.textContent = 'Opening the Secret Formula...';

    setTimeout(() => {
      bottleStage.classList.add('fade-away');
    }, 480);

    setTimeout(() => {
      bottleStage.classList.add('hidden');
      bottleStage.classList.remove('fade-away');
      stepHint.classList.add('hidden');
      scrollCard.classList.remove('hidden');
      window.scrollTo({ top: 0, behavior: 'smooth' });
    }, 850);
  }

  function handleReset() {
    state = 'sealed';

    scrollCard.classList.add('hidden');
    scrollRoll.classList.remove('pop-out');
    corkBtn.classList.remove('popped');
    corkRing.style.display = '';

    glassBottle.classList.remove('is-interactive');
    glassBottle.setAttribute('tabindex', '-1');

    stepHint.textContent = 'Tap the cork to open the bottle';
    stepHint.classList.remove('hidden');
    bottleStage.classList.remove('hidden');

    window.scrollTo({ top: 0, behavior: 'smooth' });
  }

  corkBtn.addEventListener('click', handleUncork);

  glassBottle.addEventListener('click', handlePullScroll);
  glassBottle.addEventListener('keydown', (e) => {
    if (e.key === 'Enter' || e.key === ' ') {
      e.preventDefault();
      handlePullScroll();
    }
  });

  resetBtn.addEventListener('click', handleReset);

  createAmbientBubbles();
});
