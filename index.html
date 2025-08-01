document.addEventListener("DOMContentLoaded", function () {
  // Register plugins
  gsap.registerPlugin(SplitText, ScrambleTextPlugin, CustomEase);

  // Create custom ease for animations
  const slideEase = "cubic-bezier(0.65,0.05,0.36,1)";

  // Initialize elements
  const terminalLines = document.querySelectorAll(".terminal-line");
  const preloaderEl = document.getElementById("preloader");
  const contentEl = document.getElementById("content");

  // Special characters for scramble effect
  const specialChars = "▪";

  // Store original text content for spans that will be scrambled
  const originalTexts = {};
  document
    .querySelectorAll('.terminal-line span[data-scramble="true"]')
    .forEach(function (span, index) {
      const originalText = span.textContent;
      originalTexts[index] = originalText;
      span.setAttribute("data-original-text", originalText);
      span.textContent = "";
    });

  // Set initial state - make sure terminal lines are initially hidden
  gsap.set(".terminal-line", {
    opacity: 0
  });

  // Function to update progress bar
  function updateProgress(percent) {
    const progressBar = document.getElementById("progress-bar");
    if (progressBar) {
      progressBar.style.transition = "none";
      progressBar.style.width = percent + "%";
      
      // Add glow effect when progress is high
      if (percent > 50) {
        progressBar.style.boxShadow = `0 0 10px ${percent}px rgba(255, 10, 84, 0.3)`;
      }
    }
  }

  // Initialize system status animations
  function initializeSystemStatus() {
    const statusValues = document.querySelectorAll('.status-value[data-scramble="true"]');
    const statusIndicators = document.querySelectorAll('.status-indicator');
    
    // Animate status values with scramble effect
    statusValues.forEach((statusValue, index) => {
      const originalText = statusValue.textContent;
      const finalTexts = ['READY', 'CONNECTED', 'LOADED'];
      
      gsap.to(statusValue, {
        duration: 1.5,
        scrambleText: {
          text: finalTexts[index],
          chars: specialChars,
          revealDelay: 0,
          speed: 0.2
        },
        ease: "none",
        delay: 2 + index * 0.5
      });
    });

    // Animate status indicators
    statusIndicators.forEach((indicator, index) => {
      gsap.to(indicator, {
        backgroundColor: '#00ff00',
        duration: 0.5,
        delay: 3 + index * 0.3,
        ease: "power2.out"
      });
    });
  }

  // Terminal preloader animation
  function animateTerminalPreloader() {
    // Reset progress to 0%
    updateProgress(0);

    // Initialize system status animations
    initializeSystemStatus();

    // Create main timeline for text animation
    const tl = gsap.timeline({
      onComplete: function () {
        // Once preloader is done, reveal the content
        revealContent();
      }
    });

    // Total animation duration in seconds
    const totalDuration = 8;

    // Get all terminal lines and sort them by top position
    const allLines = Array.from(document.querySelectorAll(".terminal-line"));
    allLines.sort((a, b) => {
      const aTop = parseInt(a.style.top);
      const bTop = parseInt(b.style.top);
      return aTop - bTop;
    });

    // Create a timeline for text reveal that's synced with progress
    const textRevealTl = gsap.timeline();

    // Process each line for text reveal
    allLines.forEach((line, lineIndex) => {
      // Set base opacity - alternating between full and reduced opacity
      const baseOpacity = lineIndex % 2 === 0 ? 1 : 0.7;

      // Calculate when this line should appear based on total duration
      // Distribute evenly across the first 80% of the animation
      const timePoint = (lineIndex / allLines.length) * (totalDuration * 0.8);

      // Reveal the line
      textRevealTl.to(
        line,
        {
          opacity: baseOpacity,
          duration: 0.3
        },
        timePoint
      );

      // Get all spans in this line that should be scrambled
      const scrambleSpans = line.querySelectorAll('span[data-scramble="true"]');

      // Apply scramble effect to each span
      scrambleSpans.forEach((span) => {
        const originalText =
          span.getAttribute("data-original-text") || span.textContent;

        // Add scramble effect slightly after the line appears
        textRevealTl.to(
          span,
          {
            duration: 0.8,
            scrambleText: {
              text: originalText,
              chars: specialChars,
              revealDelay: 0,
              speed: 0.3
            },
            ease: "none"
          },
          timePoint + 0.1
        );
      });
    });

    // Add the text reveal timeline to the main timeline
    tl.add(textRevealTl, 0);

    // Add enhanced progress bar animation
    tl.to({}, {
      duration: totalDuration,
      onUpdate: function() {
        const progress = (this.progress() * 100);
        updateProgress(progress);
      }
    }, 0);

    // Add periodic scramble effects throughout the animation
    for (let i = 0; i < 5; i++) {
      const randomTime = 1 + i * 1.2; // More frequent glitch effects
      tl.add(function () {
        const glitchTl = gsap.timeline();

        // Select random elements to glitch
        const allScrambleSpans = document.querySelectorAll(
          'span[data-scramble="true"]'
        );
        const randomSpans = [];

        // Select 3-5 random spans to glitch
        const numToGlitch = 3 + Math.floor(Math.random() * 3);
        for (let j = 0; j < numToGlitch; j++) {
          const randomIndex = Math.floor(
            Math.random() * allScrambleSpans.length
          );
          randomSpans.push(allScrambleSpans[randomIndex]);
        }

        // Apply glitch effect to selected spans
        randomSpans.forEach((span) => {
          const text =
            span.textContent || span.getAttribute("data-original-text");

          // Quick scramble for glitch effect
          glitchTl.to(
            span,
            {
              duration: 0.2,
              scrambleText: {
                text: text,
                chars: specialChars,
                revealDelay: 0,
                speed: 0.1
              },
              ease: "none",
              repeat: 1
            },
            Math.random() * 0.5
          );
        });

        return glitchTl;
      }, randomTime);
    }

    // Add staggered disappearing effect at the end
    const disappearTl = gsap.timeline();

    // Add staggered disappear effect for each line
    disappearTl.to(allLines, {
      opacity: 0,
      duration: 0.2,
      stagger: 0.1, // 0.1 second between each line disappearing
      ease: "power1.in"
    });

    // Add the disappear timeline near the end of the main timeline
    tl.add(disappearTl, totalDuration - 1);

    // Set up progress bar animation that's synced with the main timeline
    tl.eventCallback("onUpdate", function () {
      const progress = Math.min(99, tl.progress() * 100);
      updateProgress(progress);
    });

    // Force final update to 100% at the end
    tl.call(
      function () {
        updateProgress(100);
      },
      [],
      totalDuration - 0.5
    );

    // Add loading completion effects
    tl.add(function() {
      // Flash effect when loading is complete
      gsap.to('.terminal-preloader', {
        backgroundColor: 'rgba(255, 10, 84, 0.1)',
        duration: 0.2,
        yoyo: true,
        repeat: 1
      });
      
      // Final status update
      gsap.to('.status-value', {
        color: '#00ff00',
        duration: 0.5,
        ease: "power2.out"
      });

      // Loading animations completion
      gsap.to('.loading-dots .dot', {
        backgroundColor: '#00ff00',
        duration: 0.3,
        stagger: 0.1,
        ease: "power2.out"
      });

      gsap.to('.loading-spinner', {
        borderTopColor: '#00ff00',
        duration: 0.3,
        ease: "power2.out"
      });

      gsap.to('.loading-pulse', {
        backgroundColor: '#00ff00',
        duration: 0.3,
        ease: "power2.out"
      });
    }, totalDuration - 0.3);

    return tl;
  }

  // Reveal content by transitioning the preloader out
  function revealContent() {
    const titleLines = document.querySelectorAll(
      ".quote-section .title-line span"
    );

    // Create timeline for content reveal
    const revealTl = gsap.timeline();

    // Clip the preloader from bottom to top (similar to menu animation)
    revealTl.to(preloaderEl, {
      clipPath: "polygon(0% 0%, 100% 0%, 100% 0%, 0% 0%)",
      duration: 0.64,
      ease: slideEase,
      onComplete: () => {
        // Remove preloader after animation
        preloaderEl.style.display = "none";
      }
    });

    // Show the content
    revealTl.to(
      contentEl,
      {
        opacity: 1,
        visibility: "visible",
        duration: 0.3
      },
      "-=0.3"
    );

    // Initialize SplitText after content is visible
    revealTl.call(() => {
      // Initialize SplitText on nav links
      const navLinks = document.querySelectorAll(".nav-link");
      navLinks.forEach((link) => {
        // Create new SplitText instance with new features
        const splitLink = new SplitText(link, {
          type: "chars",
          charsClass: "char",
          position: "relative",
          linesClass: "line",
          deepSlice: true,
          propIndex: true
        });

        // Store the SplitText instance on the element
        link._splitText = splitLink;

        // Setup hover effect
        link.addEventListener("mouseenter", () => {
          gsap.to(splitLink.chars, {
            x: (i) => `${0.5 + i * 0.1}em`,
            duration: 0.64,
            ease: slideEase,
            stagger: {
              each: 0.015,
              from: "start"
            }
          });
        });

        link.addEventListener("mouseleave", () => {
          gsap.to(splitLink.chars, {
            x: 0,
            duration: 0.64,
            ease: slideEase,
            stagger: {
              each: 0.01,
              from: "end"
            }
          });
        });
      });
    });

    // Animate the title lines
    revealTl.to(
      titleLines,
      {
        y: "0%",
        duration: 0.64,
        stagger: 0.1,
        ease: slideEase
      },
      "-=0.2"
    );
  }

  // Initialize menu functionality
  function initializeMenu() {
    // Elements
    const menuBtn = document.getElementById("menu-btn");
    const closeBtn = document.getElementById("close-btn");
    const overlay = document.getElementById("overlay");
    const featuredImage = document.getElementById("featured-image");
    const brandLogo = document.querySelector(".brand .text-reveal a");
    const primaryNav = document.querySelector(".primary-nav .grid");
    const overlayBrand = document.querySelector(
      ".overlay-brand .text-reveal a"
    );
    const overlayClose = document.querySelector(".close-toggle .text-reveal p");
    const navLinks = document.querySelectorAll(".nav-link");
    const footerItems = document.querySelectorAll(
      ".overlay-footer .text-reveal p, .overlay-footer .text-reveal a"
    );
    const titleLines = document.querySelectorAll(
      ".quote-section .title-line span"
    );

    let isAnimating = false;

    // Initial setup
    gsap.set(overlay, {
      clipPath: "polygon(0% 100%, 100% 100%, 100% 100%, 0% 100%)",
      pointerEvents: "none"
    });

    gsap.set(featuredImage, {
      clipPath: "polygon(0% 100%, 100% 100%, 100% 100%, 0% 100%)"
    });

    gsap.set([overlayBrand, overlayClose], {
      y: "100%"
    });

    gsap.set(".nav-link", {
      y: "100%"
    });

    gsap.set(footerItems, {
      y: "100%"
    });

    // Open menu function
    function openMenu() {
      if (isAnimating) return;
      isAnimating = true;

      const tl = gsap.timeline({
        onComplete: () => (isAnimating = false)
      });

      // Hide the title lines with staggered animation
      tl.to(titleLines, {
        y: "100%",
        duration: 0.64,
        stagger: 0.075,
        ease: slideEase
      });

      tl.to(
        [brandLogo, menuBtn],
        {
          y: "-100%",
          duration: 0.64,
          stagger: 0.1,
          ease: slideEase,
          onComplete: () => {
            primaryNav.style.pointerEvents = "none";
            gsap.set([brandLogo, menuBtn], {
              y: "100%"
            });
          }
        },
        "-=0.4"
      );

      tl.to(
        overlay,
        {
          clipPath: "polygon(0% 0%, 100% 0%, 100% 100%, 0% 100%)",
          duration: 0.64,
          ease: slideEase,
          onStart: () => {
            overlay.style.pointerEvents = "all";
          }
        },
        "-=0.4"
      );

      // First let the overlay animation complete, then animate the image from bottom to top
      tl.fromTo(
        featuredImage,
        {
          clipPath: "polygon(0% 100%, 100% 100%, 100% 100%, 0% 100%)"
        },
        {
          clipPath: "polygon(0% 0%, 100% 0%, 100% 100%, 0% 100%)",
          duration: 0.64,
          ease: slideEase
        },
        "-=0.2"
      );

      tl.to(
        [overlayBrand, overlayClose],
        {
          y: "0%",
          duration: 0.64,
          stagger: 0.1,
          ease: slideEase
        },
        "-=0.3"
      );

      tl.to(
        ".nav-link",
        {
          y: "0%",
          duration: 0.64,
          stagger: 0.075,
          ease: slideEase
        },
        "<"
      );

      tl.to(
        footerItems,
        {
          y: "0%",
          duration: 0.64,
          stagger: 0.1,
          ease: slideEase
        },
        "<"
      );
    }

    // Close menu function
    function closeMenu() {
      if (isAnimating) return;
      isAnimating = true;

      const tl = gsap.timeline({
        onComplete: () => {
          isAnimating = false;
        }
      });

      tl.to([overlayBrand, overlayClose], {
        y: "-100%",
        duration: 0.64,
        stagger: 0.1,
        ease: slideEase
      });

      tl.to(
        ".nav-link",
        {
          y: "-100%",
          duration: 0.64,
          stagger: 0.05,
          ease: slideEase
        },
        "<"
      );

      // Make sure all footer items are animated, including social links
      tl.to(
        footerItems,
        {
          y: "-100%",
          duration: 0.64,
          stagger: 0.05,
          ease: slideEase
        },
        "<"
      );

      // Animate the featured image to close from top to bottom
      tl.to(
        featuredImage,
        {
          clipPath: "polygon(0% 100%, 100% 100%, 100% 100%, 0% 100%)",
          duration: 0.64,
          ease: slideEase
        },
        "-=0.64"
      );

      tl.to(
        overlay,
        {
          clipPath: "polygon(0% 0%, 100% 0%, 100% 0%, 0% 0%)",
          duration: 0.64,
          ease: slideEase,
          onComplete: () => {
            overlay.style.pointerEvents = "none";
            gsap.set(overlay, {
              clipPath: "polygon(0% 100%, 100% 100%, 100% 100%, 0% 100%)"
            });
            gsap.set(featuredImage, {
              clipPath: "polygon(0% 100%, 100% 100%, 100% 100%, 0% 100%)"
            });
            gsap.set([overlayBrand, overlayClose], {
              y: "100%"
            });
            gsap.set(".nav-link", {
              y: "100%"
            });
            gsap.set(footerItems, {
              y: "100%"
            });
          }
        },
        "+=0.2"
      );

      tl.to(
        [brandLogo, menuBtn],
        {
          y: "0%",
          duration: 0.64,
          stagger: 0.1,
          ease: slideEase,
          onStart: () => {
            primaryNav.style.pointerEvents = "all";
          }
        },
        "-=0.3"
      );

      // Show the title lines with staggered animation
      tl.to(
        titleLines,
        {
          y: "0%",
          duration: 0.64,
          stagger: 0.075,
          ease: slideEase
        },
        "-=0.4"
      );
    }

    // Event listeners
    menuBtn.addEventListener("click", openMenu);
    closeBtn.addEventListener("click", closeMenu);

    // Menu item click handlers
    navLinks.forEach((link) => {
      link.addEventListener("click", (e) => {
        e.preventDefault();
        closeMenu();
      });
    });
  }

  // Setup initial preloader state
  gsap.set(preloaderEl, {
    clipPath: "polygon(0% 0%, 100% 0%, 100% 100%, 0% 100%)"
  });

  // Set initial state for title lines
  const titleLines = document.querySelectorAll(
    ".quote-section .title-line span"
  );
  gsap.set(titleLines, {
    y: "100%"
  });

  // Start terminal preloader animation
  const terminalAnimation = animateTerminalPreloader();

  // Initialize menu functionality
  initializeMenu();

  // Initialize Interactive Text Animation after content is revealed
  function initializeInteractiveTextAnimation() {
    CustomEase.create("customEase", "0.86, 0, 0.07, 1");
    CustomEase.create("mouseEase", "0.25, 0.1, 0.25, 1");

    document.fonts.ready.then(() => {
      initializeAnimation();
    });

    function initializeAnimation() {
      const backgroundTextItems = document.querySelectorAll(".text-item");
      const backgroundImages = {
        BLOGSITE: document.getElementById("default-bg"),
        アニメ: document.getElementById("focus-bg"),
        HACKING: document.getElementById("presence-bg"),
        default: document.getElementById("default-bg")
      };

      function switchBackgroundImage(id) {
        Object.values(backgroundImages).forEach((bg) => {
          gsap.to(bg, {
            opacity: 0,
            duration: 0.8,
            ease: "customEase"
          });
        });

        if (backgroundImages[id]) {
          gsap.to(backgroundImages[id], {
            opacity: 1,
            duration: 0.8,
            ease: "customEase",
            delay: 0.2
          });
        } else {
          gsap.to(backgroundImages.default, {
            opacity: 1,
            duration: 0.8,
            ease: "customEase",
            delay: 0.2
          });
        }
      }

      const alternativeTexts = {
        アニメ: {
          BE: "BECOME",
          PRESENT: "MINDFUL",
          LISTEN: "HEAR",
          DEEPLY: "INTENTLY",
          OBSERVE: "NOTICE",
          "&": "+",
          FEEL: "SENSE",
          MAKE: "CREATE",
          BETTER: "IMPROVED",
          DECISIONS: "CHOICES",
          THE: "YOUR",
          CREATIVE: "ARTISTIC",
          PROCESS: "JOURNEY",
          IS: "FEELS",
          MYSTERIOUS: "MAGICAL",
          S: "START",
          I: "INSPIRE",
          M: "MAKE",
          P: "PURE",
          L: "LIGHT",
          C: "CREATE",
          T: "TRANSFORM",
          Y: "YOURS",
          "IS THE KEY": "UNLOCKS ALL",
          "FIND YOUR VOICE": "SPEAK YOUR TRUTH",
          "TRUST INTUITION": "FOLLOW INSTINCT",
          "EMBRACE SILENCE": "WELCOME STILLNESS",
          "QUESTION EVERYTHING": "CHALLENGE NORMS",
          TRUTH: "HONESTY",
          WISDOM: "INSIGHT",
          FOCUS: "CONCENTRATE",
          ATTENTION: "AWARENESS",
          AWARENESS: "CONSCIOUSNESS",
          PRESENCE: "BEING",
          SIMPLIFY: "MINIMIZE",
          REFINE: "PERFECT"
        },
        HACKING: {
          BE: "EVOLVE",
          PRESENT: "ENGAGED",
          LISTEN: "ABSORB",
          DEEPLY: "FULLY",
          OBSERVE: "ANALYZE",
          "&": "→",
          FEEL: "EXPERIENCE",
          MAKE: "BUILD",
          BETTER: "STRONGER",
          DECISIONS: "SYSTEMS",
          THE: "EACH",
          CREATIVE: "ITERATIVE",
          PROCESS: "METHOD",
          IS: "BECOMES",
          MYSTERIOUS: "REVEALING",
          S: "STRUCTURE",
          I: "ITERATE",
          M: "METHOD",
          P: "PRACTICE",
          L: "LEARN",
          C: "CONSTRUCT",
          T: "TECHNIQUE",
          Y: "YIELD",
          "IS THE KEY": "DRIVES SUCCESS",
          "FIND YOUR VOICE": "DEVELOP YOUR STYLE",
          "TRUST INTUITION": "FOLLOW THE FLOW",
          "EMBRACE SILENCE": "VALUE PAUSES",
          "QUESTION EVERYTHING": "EXAMINE DETAILS",
          TRUTH: "CLARITY",
          WISDOM: "KNOWLEDGE",
          FOCUS: "DIRECTION",
          ATTENTION: "PRECISION",
          AWARENESS: "UNDERSTANDING",
          PRESENCE: "ENGAGEMENT",
          SIMPLIFY: "STREAMLINE",
          REFINE: "OPTIMIZE"
        },
        BLOGSITE: {
          BE: "SEE",
          PRESENT: "FOCUSED",
          LISTEN: "UNDERSTAND",
          DEEPLY: "CLEARLY",
          OBSERVE: "PERCEIVE",
          "&": "=",
          FEEL: "KNOW",
          MAKE: "ACHIEVE",
          BETTER: "CLEARER",
          DECISIONS: "VISION",
          THE: "THIS",
          CREATIVE: "INSIGHTFUL",
          PROCESS: "THINKING",
          IS: "BRINGS",
          MYSTERIOUS: "ILLUMINATING",
          S: "SHARP",
          I: "INSIGHT",
          M: "MINDFUL",
          P: "PRECISE",
          L: "LUCID",
          C: "CLEAR",
          T: "TRANSPARENT",
          Y: "YES",
          "IS THE KEY": "REVEALS TRUTH",
          "FIND YOUR VOICE": "DISCOVER YOUR VISION",
          "TRUST INTUITION": "BELIEVE YOUR EYES",
          "EMBRACE SILENCE": "SEEK STILLNESS",
          "QUESTION EVERYTHING": "CLARIFY ASSUMPTIONS",
          TRUTH: "REALITY",
          WISDOM: "PERCEPTION",
          FOCUS: "CLARITY",
          ATTENTION: "OBSERVATION",
          AWARENESS: "RECOGNITION",
          PRESENCE: "ALERTNESS",
          SIMPLIFY: "DISTILL",
          REFINE: "SHARPEN"
        }
      };

      backgroundTextItems.forEach((item) => {
        item.dataset.originalText = item.textContent;
        item.dataset.text = item.textContent;
        gsap.set(item, { opacity: 1 });
      });

      const typeLines = document.querySelectorAll(".type-line");
      typeLines.forEach((line, index) => {
        if (index % 2 === 0) {
          line.classList.add("odd");
        } else {
          line.classList.add("even");
        }
      });

      const oddLines = document.querySelectorAll(".type-line.odd");
      const evenLines = document.querySelectorAll(".type-line.even");
      const TYPE_LINE_OPACITY = 0.015;

      const state = {
        activeRowId: null,
        kineticAnimationActive: false,
        activeKineticAnimation: null,
        textRevealAnimation: null,
        transitionInProgress: false
      };

      const textRows = document.querySelectorAll(".text-row");
      const splitTexts = {};

      textRows.forEach((row, index) => {
        const textElement = row.querySelector(".text-content");
        const text = textElement.dataset.text;
        const rowId = row.dataset.rowId;

        splitTexts[rowId] = new SplitText(textElement, {
          type: "chars",
          charsClass: "char",
          mask: true,
          reduceWhiteSpace: false,
          propIndex: true
        });

        textElement.style.visibility = "visible";
      });

      function updateCharacterWidths() {
        const isMobile = window.innerWidth < 1024;

        textRows.forEach((row, index) => {
          const rowId = row.dataset.rowId;
          const textElement = row.querySelector(".text-content");
          const computedStyle = window.getComputedStyle(textElement);
          const currentFontSize = computedStyle.fontSize;
          const chars = splitTexts[rowId].chars;

          chars.forEach((char, i) => {
            const charText =
              char.textContent ||
              (char.querySelector(".char-inner")
                ? char.querySelector(".char-inner").textContent
                : "");
            if (!charText && i === 0) return;

            let charWidth;

            if (isMobile) {
              const fontSizeValue = parseFloat(currentFontSize);
              const standardCharWidth = fontSizeValue * 0.6;
              charWidth = standardCharWidth;

              if (!char.querySelector(".char-inner") && charText) {
                char.textContent = "";
                const innerSpan = document.createElement("span");
                innerSpan.className = "char-inner";
                innerSpan.textContent = charText;
                char.appendChild(innerSpan);
                innerSpan.style.transform = "translate3d(0, 0, 0)";
              }

              char.style.width = `${charWidth}px`;
              char.style.maxWidth = `${charWidth}px`;
              char.dataset.charWidth = charWidth;
              char.dataset.hoverWidth = charWidth;
            } else {
              const tempSpan = document.createElement("span");
              tempSpan.style.position = "absolute";
              tempSpan.style.visibility = "hidden";
              tempSpan.style.fontSize = currentFontSize;
              tempSpan.style.fontFamily = "Longsile, sans-serif";
              tempSpan.textContent = charText;
              document.body.appendChild(tempSpan);

              const actualWidth = tempSpan.offsetWidth;
              document.body.removeChild(tempSpan);

              const fontSizeValue = parseFloat(currentFontSize);
              const fontSizeRatio = fontSizeValue / 160;
              const padding = 10 * fontSizeRatio;

              charWidth = Math.max(actualWidth + padding, 30 * fontSizeRatio);

              if (!char.querySelector(".char-inner") && charText) {
                char.textContent = "";
                const innerSpan = document.createElement("span");
                innerSpan.className = "char-inner";
                innerSpan.textContent = charText;
                char.appendChild(innerSpan);
                innerSpan.style.transform = "translate3d(0, 0, 0)";
              }

              char.style.width = `${charWidth}px`;
              char.style.maxWidth = `${charWidth}px`;
              char.dataset.charWidth = charWidth;

              const hoverWidth = Math.max(charWidth * 1.8, 85 * fontSizeRatio);
              char.dataset.hoverWidth = hoverWidth;
            }

            char.style.setProperty("--char-index", i);
          });
        });
      }

      updateCharacterWidths();

      window.addEventListener("resize", function () {
        clearTimeout(window.resizeTimer);
        window.resizeTimer = setTimeout(function () {
          updateCharacterWidths();
        }, 250);
      });

      textRows.forEach((row, rowIndex) => {
        const rowId = row.dataset.rowId;
        const chars = splitTexts[rowId].chars;

        gsap.set(chars, {
          opacity: 0,
          filter: "blur(15px)"
        });

        gsap.to(chars, {
          opacity: 1,
          filter: "blur(0px)",
          duration: 0.8,
          stagger: 0.09,
          ease: "customEase",
          delay: 0.15 * rowIndex
        });
      });

      function forceResetKineticAnimation() {
        if (state.activeKineticAnimation) {
          state.activeKineticAnimation.kill();
          state.activeKineticAnimation = null;
        }

        const kineticType = document.getElementById("kinetic-type");
        gsap.killTweensOf([kineticType, typeLines, oddLines, evenLines]);

        gsap.set(kineticType, {
          display: "grid",
          scale: 1,
          rotation: 0,
          opacity: 1,
          visibility: "visible"
        });

        gsap.set(typeLines, {
          opacity: TYPE_LINE_OPACITY,
          x: "0%"
        });

        state.kineticAnimationActive = false;
      }

      function startKineticAnimation(text) {
        forceResetKineticAnimation();

        const kineticType = document.getElementById("kinetic-type");
        kineticType.style.display = "grid";
        kineticType.style.opacity = "1";
        kineticType.style.visibility = "visible";

        const repeatedText = `${text} ${text} ${text}`;

        typeLines.forEach((line) => {
          line.textContent = repeatedText;
        });

        setTimeout(() => {
          const timeline = gsap.timeline({
            onComplete: () => {
              state.kineticAnimationActive = false;
            }
          });

          timeline.to(kineticType, {
            duration: 5,
            ease: "customEase",
            scale: -1,
            rotation: 0
          });

          timeline.to(
            oddLines,
            {
              keyframes: [
                { x: "20%", duration: 1, ease: "customEase" },
                { x: "200%", duration: 1.5, ease: "customEase" }
              ],
              stagger: 0.08
            },
            0
          );

          timeline.to(
            evenLines,
            {
              keyframes: [
                { x: "-20%", duration: 1, ease: "customEase" },
                { x: "-200%", duration: 1.5, ease: "customEase" },
              ],
              stagger: 0.08
            },
            0
          );

          timeline.to(
            typeLines,
            {
              keyframes: [
                { opacity: 1, duration: 1, ease: "customEase" },
                { opacity: 0, duration: 1, ease: "customEase" }
              ],
              stagger: 0.05
            },
            0
          );

          state.kineticAnimationActive = true;
          state.activeKineticAnimation = timeline;
        }, 20);
      }

      function fadeOutKineticAnimation() {
        if (!state.kineticAnimationActive) return;

        if (state.activeKineticAnimation) {
          state.activeKineticAnimation.kill();
          state.activeKineticAnimation = null;
        }

        const kineticType = document.getElementById("kinetic-type");

        const fadeOutTimeline = gsap.timeline({
          onComplete: () => {
            gsap.set(kineticType, {
              scale: 1,
              rotation: 0,
              opacity: 1
            });

            gsap.set(typeLines, {
              opacity: TYPE_LINE_OPACITY,
              x: "0%"
            });

            state.kineticAnimationActive = false;
          }
        });

        fadeOutTimeline.to(kineticType, {
          opacity: 0,
          scale: 0.8,
          duration: 0.5,
          ease: "customEase"
        });
      }

      function transitionBetweenRows(fromRow, toRow) {
        if (state.transitionInProgress) return;

        state.transitionInProgress = true;

        const fromRowId = fromRow.dataset.rowId;
        const toRowId = toRow.dataset.rowId;

        fromRow.classList.remove("active");
        const fromChars = splitTexts[fromRowId].chars;
        const fromInners = fromRow.querySelectorAll(".char-inner");

        gsap.killTweensOf(fromChars);
        gsap.killTweensOf(fromInners);

        toRow.classList.add("active");
        state.activeRowId = toRowId;

        const toText = toRow.querySelector(".text-content").dataset.text;
        const toChars = splitTexts[toRowId].chars;
        const toInners = toRow.querySelectorAll(".char-inner");

        forceResetKineticAnimation();
        switchBackgroundImage(toRowId);
        startKineticAnimation(toText);

        if (state.textRevealAnimation) {
          state.textRevealAnimation.kill();
        }
        state.textRevealAnimation = createTextRevealAnimation(toRowId);

        gsap.set(fromChars, {
          maxWidth: (i, target) => parseFloat(target.dataset.charWidth)
        });

        gsap.set(fromInners, {
          x: 0
        });

        const timeline = gsap.timeline({
          onComplete: () => {
            state.transitionInProgress = false;
          }
        });

        timeline.to(
          toChars,
          {
            maxWidth: (i, target) => parseFloat(target.dataset.hoverWidth),
            duration: 0.64,
            stagger: 0.04,
            ease: "customEase"
          },
          0
        );

        timeline.to(
          toInners,
          {
            x: -35,
            duration: 0.64,
            stagger: 0.04,
            ease: "customEase"
          },
          0.05
        );
      }

      function createTextRevealAnimation(rowId) {
        const timeline = gsap.timeline();

        timeline.to(backgroundTextItems, {
          opacity: 0.3,
          duration: 0.5,
          ease: "customEase"
        });

        timeline.call(() => {
          backgroundTextItems.forEach((item) => {
            item.classList.add("highlight");
          });
        });

        timeline.call(
          () => {
            backgroundTextItems.forEach((item) => {
              const originalText = item.dataset.text;
              if (
                alternativeTexts[rowId] &&
                alternativeTexts[rowId][originalText]
              ) {
                item.textContent = alternativeTexts[rowId][originalText];
              }
            });
          },
          null,
          "+=0.5"
        );

        timeline.call(() => {
          backgroundTextItems.forEach((item) => {
            item.classList.remove("highlight");
            item.classList.add("highlight-reverse");
          });
        });

        timeline.call(
          () => {
            backgroundTextItems.forEach((item) => {
              item.classList.remove("highlight-reverse");
            });
          },
          null,
          "+=0.5"
        );

        return timeline;
      }

      function resetBackgroundTextWithAnimation() {
        const timeline = gsap.timeline();

        timeline.call(() => {
          backgroundTextItems.forEach((item) => {
            item.classList.add("highlight");
          });
        });

        timeline.call(
          () => {
            backgroundTextItems.forEach((item) => {
              item.textContent = item.dataset.originalText;
            });
          },
          null,
          "+=0.5"
        );

        timeline.call(() => {
          backgroundTextItems.forEach((item) => {
            item.classList.remove("highlight");
            item.classList.add("highlight-reverse");
          });
        });

        timeline.call(
          () => {
            backgroundTextItems.forEach((item) => {
              item.classList.remove("highlight-reverse");
            });
          },
          null,
          "+=0.5"
        );

        timeline.to(backgroundTextItems, {
          opacity: 1,
          duration: 0.5,
          ease: "customEase"
        });

        return timeline;
      }

      function activateRow(row) {
        const rowId = row.dataset.rowId;

        if (state.activeRowId === rowId) return;
        if (state.transitionInProgress) return;

        const activeRow = document.querySelector(".text-row.active");

        if (activeRow) {
          transitionBetweenRows(activeRow, row);
        } else {
          row.classList.add("active");
          state.activeRowId = rowId;

          const text = row.querySelector(".text-content").dataset.text;
          const chars = splitTexts[rowId].chars;
          const innerSpans = row.querySelectorAll(".char-inner");

          switchBackgroundImage(rowId);
          startKineticAnimation(text);

          if (state.textRevealAnimation) {
            state.textRevealAnimation.kill();
          }
          state.textRevealAnimation = createTextRevealAnimation(rowId);

          const timeline = gsap.timeline();

          timeline.to(
            chars,
            {
              maxWidth: (i, target) => parseFloat(target.dataset.hoverWidth),
              duration: 0.64,
              stagger: 0.04,
              ease: "customEase"
            },
            0
          );

          timeline.to(
            innerSpans,
            {
              x: -35,
              duration: 0.64,
              stagger: 0.04,
              ease: "customEase"
            },
            0.05
          );
        }
      }

      function deactivateRow(row) {
        const rowId = row.dataset.rowId;

        if (state.activeRowId !== rowId) return;
        if (state.transitionInProgress) return;

        state.activeRowId = null;
        row.classList.remove("active");

        switchBackgroundImage("default");
        fadeOutKineticAnimation();

        if (state.textRevealAnimation) {
          state.textRevealAnimation.kill();
        }
        state.textRevealAnimation = resetBackgroundTextWithAnimation();

        const chars = splitTexts[rowId].chars;
        const innerSpans = row.querySelectorAll(".char-inner");

        const timeline = gsap.timeline();

        timeline.to(
          innerSpans,
          {
            x: 0,
            duration: 0.64,
            stagger: 0.03,
            ease: "customEase"
          },
          0
        );

        timeline.to(
          chars,
          {
            maxWidth: (i, target) => parseFloat(target.dataset.charWidth),
            duration: 0.64,
            stagger: 0.03,
            ease: "customEase"
          },
          0.05
        );
      }

      function initializeParallax() {
        const container = document.querySelector("body");
        const backgroundElements = [
          ...document.querySelectorAll("[id$='-bg']"),
          ...document.querySelectorAll(".bg-text-container")
        ];

        const parallaxLayers = [0.02, 0.03, 0.04, 0.05];
        backgroundElements.forEach((el, index) => {
          el.dataset.parallaxSpeed =
            parallaxLayers[index % parallaxLayers.length];

          gsap.set(el, {
            transformOrigin: "center center",
            force3D: true
          });
        });

        let lastParallaxTime = 0;
        const throttleParallax = 20;

        container.addEventListener("mousemove", (e) => {
          const now = Date.now();
          if (now - lastParallaxTime < throttleParallax) return;
          lastParallaxTime = now;

          const centerX = window.innerWidth / 2;
          const centerY = window.innerHeight / 2;
          const offsetX = (e.clientX - centerX) / centerX;
          const offsetY = (e.clientY - centerY) / centerY;

          backgroundElements.forEach((el) => {
            const speed = parseFloat(el.dataset.parallaxSpeed);

            if (el.id && el.id.endsWith("-bg") && el.style.opacity === "0") {
              return;
            }

            const moveX = offsetX * 100 * speed;
            const moveY = offsetY * 50 * speed;

            gsap.to(el, {
              x: moveX,
              y: moveY,
              duration: 1.0,
              ease: "mouseEase",
              overwrite: "auto"
            });
          });
        });

        container.addEventListener("mouseleave", () => {
          backgroundElements.forEach((el) => {
            gsap.to(el, {
              x: 0,
              y: 0,
              duration: 1.5,
              ease: "customEase"
            });
          });
        });

        backgroundElements.forEach((el, index) => {
          const delay = index * 0.2;
          const floatAmount = 5 + (index % 3) * 2;

          gsap.to(el, {
            y: `+=${floatAmount}`,
            duration: 3 + (index % 2),
            ease: "sine.inOut",
            repeat: -1,
            yoyo: true,
            delay: delay
          });
        });
      }

      textRows.forEach((row) => {
        const interactiveArea = row.querySelector(".interactive-area");

        interactiveArea.addEventListener("mouseenter", () => {
          activateRow(row);
        });

        interactiveArea.addEventListener("mouseleave", () => {
          if (state.activeRowId === row.dataset.rowId) {
            deactivateRow(row);
          }
        });

        row.addEventListener("click", () => {
          activateRow(row);
        });
      });

      window.testKineticAnimation = function (rowId) {
        const row = document.querySelector(`.text-row[data-row-id="${rowId}"]`);
        if (row) {
          activateRow(row);
          setTimeout(() => {
            deactivateRow(row);
          }, 3000);
        }
      };

      function scrambleRandomText() {
        const randomIndex = Math.floor(
          Math.random() * backgroundTextItems.length
        );
        const randomItem = backgroundTextItems[randomIndex];
        const originalText = randomItem.dataset.text;

        gsap.to(randomItem, {
          duration: 1,
          scrambleText: {
            text: originalText,
            chars: "■▪▌▐▬",
            revealDelay: 0.5,
            speed: 0.3
          },
          ease: "none"
        });

        const delay = 0.5 + Math.random() * 2;
        setTimeout(scrambleRandomText, delay * 1000);
      }

      setTimeout(scrambleRandomText, 1000);

      const simplicity = document.querySelector(
        '.text-item[data-text="IS THE KEY"]'
      );
      if (simplicity) {
        const splitSimplicity = new SplitText(simplicity, {
          type: "chars",
          charsClass: "simplicity-char"
        });

        gsap.from(splitSimplicity.chars, {
          opacity: 0,
          scale: 0.5,
          duration: 1,
          stagger: 0.015,
          ease: "customEase",
          delay: 1
        });
      }

      backgroundTextItems.forEach((item, index) => {
        const delay = index * 0.1;
        gsap.to(item, {
          opacity: 0.85,
          duration: 2 + (index % 3),
          repeat: -1,
          yoyo: true,
          ease: "sine.inOut",
          delay: delay
        });
      });

      initializeParallax();

      const style = document.createElement("style");
      style.textContent = `
        #kinetic-type {
          z-index: 200 !important;
          display: grid !important;
          visibility: visible !important;
          opacity: 1;
          pointer-events: none;
        }
      `;
      document.head.appendChild(style);
    }
  }

  // Initialize interactive text animation after content is revealed
  setTimeout(() => {
initializeInteractiveTextAnimation();
initializeInteractiveFeatures();
}, 1000);

function initializeInteractiveFeatures() {
// Initialize Fancybox
Fancybox.bind("[data-fancybox]", {
  // Custom options
  dragToClose: false,
  Image: {
    zoom: true,
  },
  on: {
    initLayout: (fancybox) => {
      // Initialize Swiper when modal opens
      if (fancybox.container.querySelector('.gallery-swiper')) {
        const swiper = new Swiper('.gallery-swiper', {
          slidesPerView: 1,
          spaceBetween: 30,
          loop: true,
          autoplay: {
            delay: 5000,
            disableOnInteraction: false,
          },
          pagination: {
            el: '.swiper-pagination',
            clickable: true,
          },
          navigation: {
            nextEl: '.swiper-button-next',
            prevEl: '.swiper-button-prev',
          },
          effect: 'fade',
          fadeEffect: {
            crossFade: true
          }
        });
      }
    }
  }
});

// Modern navigation functionality
const navItems = document.querySelectorAll('.nav-item');

navItems.forEach(item => {
  item.addEventListener('click', function() {
    const action = this.getAttribute('data-action');
    
    // Remove active class from all items
    navItems.forEach(nav => nav.classList.remove('active'));
    
    // Add active class to clicked item
    this.classList.add('active');
    
    switch(action) {
      case 'about-website':
        showAboutWebsite();
        break;
      case 'guide':
        showGuide();
        break;
      case 'features':
        showFeatures();
        break;
      case 'explore-blog':
        showExploreBlog();
        break;
    }
  });
});

// Navigation action functions
function showAboutWebsite() {
  // Scroll to the first animated section (About the Website)
  if (typeof gotoSection === 'function') {
    gotoSection(0, 1);
  }
  
  // Add visual feedback
  gsap.to('.nav-item[data-action="about-website"] .shape-bg', {
    backgroundColor: 'rgba(255, 10, 84, 0.3)',
    duration: 0.3,
    ease: "power2.out"
  });
}

function showGuide() {
  // Create a modal or overlay for guide content
  const guideContent = `
    <div class="guide-modal">
      <div class="guide-content">
        <h3>How to Use This Website</h3>
        <div class="guide-steps">
          <div class="step">
            <span class="step-number">1</span>
            <div class="step-content">
              <h4>Create Your Profile</h4>
              <p>Set up your personal profile to start sharing content</p>
            </div>
          </div>
          <div class="step">
            <span class="step-number">2</span>
            <div class="step-content">
              <h4>Write Articles</h4>
              <p>Share your thoughts, tutorials, and experiences</p>
            </div>
          </div>
          <div class="step">
            <span class="step-number">3</span>
            <div class="step-content">
              <h4>Engage with Community</h4>
              <p>Comment, like, and interact with other users</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  `;
  
  // Add modal to page
  document.body.insertAdjacentHTML('beforeend', guideContent);
  
  // Animate modal in
  gsap.fromTo('.guide-modal', 
    { opacity: 0, scale: 0.8 },
    { opacity: 1, scale: 1, duration: 0.5, ease: "back.out(1.7)" }
  );
  
  // Close modal on click outside
  document.querySelector('.guide-modal').addEventListener('click', function(e) {
    if (e.target === this) {
      gsap.to('.guide-modal', {
        opacity: 0,
        scale: 0.8,
        duration: 0.3,
        ease: "power2.in",
        onComplete: () => this.remove()
      });
    }
  });
}

function showFeatures() {
  // Create features showcase
  const featuresContent = `
    <div class="features-modal">
      <div class="features-content">
        <h3>Website Features</h3>
        <div class="features-grid">
          <div class="feature-card">
            <i class='bx bx-edit-alt'></i>
            <h4>Content Creation</h4>
            <p>Create and share amazing articles</p>
          </div>
          <div class="feature-card">
            <i class='bx bx-group'></i>
            <h4>Community</h4>
            <p>Connect with like-minded people</p>
          </div>
          <div class="feature-card">
            <i class='bx bx-palette'></i>
            <h4>Customization</h4>
            <p>Personalize your experience</p>
          </div>
        </div>
      </div>
    </div>
  `;
  
  document.body.insertAdjacentHTML('beforeend', featuresContent);
  
  gsap.fromTo('.features-modal', 
    { opacity: 0, y: 50 },
    { opacity: 1, y: 0, duration: 0.5, ease: "power2.out" }
  );
  
  document.querySelector('.features-modal').addEventListener('click', function(e) {
    if (e.target === this) {
      gsap.to('.features-modal', {
        opacity: 0,
        y: 50,
        duration: 0.3,
        ease: "power2.in",
        onComplete: () => this.remove()
      });
    }
  });
}

function showExploreBlog() {
  // Trigger the existing gallery modal
  const galleryTrigger = document.querySelector('.gallery-trigger');
  if (galleryTrigger) {
    galleryTrigger.click();
  }
}
}

function toggleMusic() {
const btn = document.querySelector('[data-action="play-music"]');
const icon = btn.querySelector('i');
const text = btn.querySelector('span');

if (btn.classList.contains('active')) {
  btn.classList.remove('active');
  icon.className = 'bx bx-music';
  text.textContent = 'Play Music';
  // Stop music logic here
} else {
  btn.classList.add('active');
  icon.className = 'bx bx-pause';
  text.textContent = 'Pause Music';
  // Play music logic here
}
}

function toggleParticles() {
const btn = document.querySelector('[data-action="show-particles"]');

if (btn.classList.contains('active')) {
  btn.classList.remove('active');
  // Remove particles
  const particles = document.querySelector('.particles-container');
  if (particles) particles.remove();
} else {
  btn.classList.add('active');
  // Create particles
  createParticles();
}
}

function createParticles() {
const particlesContainer = document.createElement('div');
particlesContainer.className = 'particles-container';
particlesContainer.style.cssText = `
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 1000;
`;

for (let i = 0; i < 50; i++) {
  const particle = document.createElement('div');
  particle.style.cssText = `
    position: absolute;
    width: 4px;
    height: 4px;
    background: var(--text);
    border-radius: 50%;
    animation: float ${3 + Math.random() * 4}s linear infinite;
    left: ${Math.random() * 100}%;
    animation-delay: ${Math.random() * 2}s;
  `;
  particlesContainer.appendChild(particle);
}

document.body.appendChild(particlesContainer);

// Add floating animation
const style = document.createElement('style');
style.textContent = `
  @keyframes float {
    0% {
      transform: translateY(100vh) rotate(0deg);
      opacity: 0;
    }
    10% {
      opacity: 1;
    }
    90% {
      opacity: 1;
    }
    100% {
      transform: translateY(-100px) rotate(360deg);
      opacity: 0;
    }
  }
`;
document.head.appendChild(style);
}

function changeTheme() {
const themes = [
  { text: '#ffcc00', bg: '#000000' },
  { text: '#00ff88', bg: '#1a1a1a' },
  { text: '#ff6b6b', bg: '#0a0a0a' },
  { text: '#4ecdc4', bg: '#1a1a1a' },
  { text: '#45b7d1', bg: '#0f0f0f' }
];

const currentTheme = document.documentElement.style.getPropertyValue('--text') || '#ffcc00';
const currentIndex = themes.findIndex(theme => theme.text === currentTheme);
const nextIndex = (currentIndex + 1) % themes.length;
const newTheme = themes[nextIndex];

document.documentElement.style.setProperty('--text', newTheme.text);
document.documentElement.style.setProperty('--bg', newTheme.bg);

// Animate theme change
gsap.to('body', {
  backgroundColor: newTheme.bg,
  duration: 0.5,
  ease: 'power2.out'
});
}

  // Initialize AOS (Animate On Scroll)
  AOS.init({
    duration: 1000,
    easing: 'ease-in-out',
    once: true,
    mirror: false
  });

  // Initialize counter animations
  function initializeCounters() {
    const counters = document.querySelectorAll('.stat-number');
    
    const observerOptions = {
      threshold: 0.5,
      rootMargin: '0px 0px -100px 0px'
    };

    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          const counter = entry.target;
          const target = parseInt(counter.getAttribute('data-count'));
          const duration = 2000;
          const step = target / (duration / 16);
          let current = 0;

          const timer = setInterval(() => {
            current += step;
            if (current >= target) {
              current = target;
              clearInterval(timer);
            }
            counter.textContent = Math.floor(current);
          }, 16);
          
          observer.unobserve(counter);
        }
      });
    }, observerOptions);

    counters.forEach(counter => {
      observer.observe(counter);
    });
  }

  // Initialize counters when page loads
  setTimeout(() => {
    initializeCounters();
  }, 1500);

  // Button click handlers
  window.scrollToContact = function() {
    // Scroll to contact section (you can add this later)
    console.log('Scroll to contact section');
  };

  window.viewPortfolio = function() {
    // Open portfolio (you can add this later)
    console.log('View portfolio');
  };

  // Smooth scroll for navigation
  function initializeSmoothScroll() {
    const links = document.querySelectorAll('a[href^="#"]');
    
    links.forEach(link => {
      link.addEventListener('click', function(e) {
        e.preventDefault();
        
        const targetId = this.getAttribute('href');
        const targetSection = document.querySelector(targetId);
        
        if (targetSection) {
          targetSection.scrollIntoView({
            behavior: 'smooth',
            block: 'start'
          });
        }
      });
    });
  }

  // Initialize smooth scroll
  initializeSmoothScroll();

  // Animated Sections with GSAP
  function initializeAnimatedSections() {
    // Register Observer plugin
    gsap.registerPlugin(Observer);

    let sections = document.querySelectorAll("section.first, section.second, section.third, section.fourth, section.fifth, section.sixth, section.seventh, section.eighth, section.ninth, section.tenth"),
      images = document.querySelectorAll("section.first .bg, section.second .bg, section.third .bg, section.fourth .bg, section.fifth .bg, section.sixth .bg, section.seventh .bg, section.eighth .bg, section.ninth .bg, section.tenth .bg"),
      headings = gsap.utils.toArray(".section-heading"),
      outerWrappers = gsap.utils.toArray("section.first .outer, section.second .outer, section.third .outer, section.fourth .outer, section.fifth .outer, section.sixth .outer, section.seventh .outer, section.eighth .outer, section.ninth .outer, section.tenth .outer"),
      innerWrappers = gsap.utils.toArray("section.first .inner, section.second .inner, section.third .inner, section.fourth .inner, section.fifth .inner, section.sixth .inner, section.seventh .inner, section.eighth .inner, section.ninth .inner, section.tenth .inner"),
      splitHeadings = headings.map(heading => new SplitText(heading, { type: "chars,words,lines", linesClass: "clip-text" })),
      currentIndex = -1,
      animating,
      bannerSection = document.getElementById("interactive-banner"),
      hasStartedScrolling = false;

    // Set initial states
    gsap.set(outerWrappers, { yPercent: 100 });
    gsap.set(innerWrappers, { yPercent: -100 });
    gsap.set(sections, { autoAlpha: 0, zIndex: 0 });

    function gotoSection(index, direction) {
      // Check if we're trying to go beyond boundaries
      if (index < 0) {
        // Going up from first section - show banner
        if (currentIndex === 0) {
          animating = true;
          let tl = gsap.timeline({
            defaults: { duration: 1.25, ease: "power1.inOut" },
            onComplete: () => animating = false
          });
          
          // Hide current section
          gsap.set(sections[currentIndex], { zIndex: 0 });
          tl.to(images[currentIndex], { yPercent: 15 })
            .set(sections[currentIndex], { autoAlpha: 0 });
          
          // Show banner
          tl.to(bannerSection, { 
            autoAlpha: 1, 
            duration: 0.8, 
            ease: "power2.inOut" 
          }, 0.2);
          
          currentIndex = -1;
          hasStartedScrolling = false;
        }
        return; // Don't proceed if trying to go below 0
      }
      
      if (index >= sections.length) {
        return; // Don't proceed if trying to go beyond last section
      }
      
      animating = true;
      let fromTop = direction === -1,
          dFactor = fromTop ? -1 : 1,
          tl = gsap.timeline({
            defaults: { duration: 1.25, ease: "power1.inOut" },
            onComplete: () => animating = false
          });

      // If this is the first scroll and we're going down, hide the banner
      if (currentIndex === -1 && direction === 1 && !hasStartedScrolling) {
        hasStartedScrolling = true;
        tl.to(bannerSection, { 
          autoAlpha: 0, 
          duration: 0.8, 
          ease: "power2.inOut" 
        }, 0);
      }

      if (currentIndex >= 0) {
        // The first time this function runs, current is -1
        gsap.set(sections[currentIndex], { zIndex: 0 });
        tl.to(images[currentIndex], { yPercent: -15 * dFactor })
          .set(sections[currentIndex], { autoAlpha: 0 });
      }
      
      gsap.set(sections[index], { autoAlpha: 1, zIndex: 1 });
      tl.fromTo([outerWrappers[index], innerWrappers[index]], { 
          yPercent: i => i ? -100 * dFactor : 100 * dFactor
        }, { 
          yPercent: 0 
        }, 0)
        .fromTo(images[index], { yPercent: 15 * dFactor }, { yPercent: 0 }, 0)
        .fromTo(splitHeadings[index].chars, { 
            autoAlpha: 0, 
            yPercent: 150 * dFactor
        }, {
            autoAlpha: 1,
            yPercent: 0,
            duration: 1,
            ease: "power2",
            stagger: {
              each: 0.02,
              from: "random"
            }
          }, 0.2);

      currentIndex = index;
    }

    Observer.create({
      type: "wheel,touch,pointer",
      wheelSpeed: -1,
      onDown: () => !animating && gotoSection(currentIndex - 1, -1),
      onUp: () => !animating && gotoSection(currentIndex + 1, 1),
      tolerance: 10,
      preventDefault: true
    });

  }


  setTimeout(() => {
    initializeAnimatedSections();
  }, 2000);
  
  // Initialize AOS (Animate On Scroll)
  if (typeof AOS !== 'undefined') {
    AOS.init({
      duration: 800,
      easing: 'ease-in-out',
      once: true,
      mirror: false,
      offset: 100
    });
  }
});

// Explore Features Function
function exploreFeatures() {
  // Create a fancy modal to showcase features
  if (typeof Fancybox !== 'undefined') {
    Fancybox.show([
      {
        src: `
          <div class="feature-modal">
            <h2>🚀 Explore BlogNimeHack Features</h2>
            <div class="feature-grid">
              <div class="modal-feature">
                <i class='bx bx-palette'></i>
                <h3>Anime Theme</h3>
                <p>Beautiful anime-inspired design with customizable themes</p>
              </div>
              <div class="modal-feature">
                <i class='bx bx-shield-check'></i>
                <h3>Security First</h3>
                <p>Advanced security features to protect your data</p>
              </div>
              <div class="modal-feature">
                <i class='bx bx-mobile-alt'></i>
                <h3>Mobile Optimized</h3>
                <p>Perfect experience on all devices</p>
              </div>
              <div class="modal-feature">
                <i class='bx bx-world'></i>
                <h3>Global Community</h3>
                <p>Connect with developers worldwide</p>
              </div>
            </div>
            <div class="modal-cta">
              <button onclick="Fancybox.close()" class="close-btn">Close</button>
              <button onclick="window.location.href='#about'" class="learn-more-btn">Learn More</button>
            </div>
          </div>
        `,
        type: 'html'
      }
    ], {
      on: {
        done: () => {
          // Add styles for the modal content
          const style = document.createElement('style');
          style.textContent = `
            .feature-modal {
              background: linear-gradient(135deg, #1a1e23, #2a2e33);
              color: #ffe0e0;
              padding: 2rem;
              border-radius: 20px;
              max-width: 600px;
              text-align: center;
            }
            .feature-modal h2 {
              color: #ff0a54;
              margin-bottom: 2rem;
              font-size: 2rem;
            }
            .feature-grid {
              display: grid;
              grid-template-columns: repeat(2, 1fr);
              gap: 1.5rem;
              margin-bottom: 2rem;
            }
            .modal-feature {
              background: rgba(255, 255, 255, 0.05);
              border: 1px solid rgba(255, 255, 255, 0.1);
              border-radius: 12px;
              padding: 1.5rem;
              transition: all 0.3s ease;
            }
            .modal-feature:hover {
              transform: translateY(-5px);
              border-color: #ff0a54;
            }
            .modal-feature i {
              font-size: 2rem;
              color: #ff0a54;
              margin-bottom: 1rem;
              display: block;
            }
            .modal-feature h3 {
              color: #ffe0e0;
              margin-bottom: 0.5rem;
            }
            .modal-feature p {
              color: #c5babf;
              font-size: 0.9rem;
            }
            .modal-cta {
              display: flex;
              gap: 1rem;
              justify-content: center;
            }
            .close-btn, .learn-more-btn {
              padding: 0.75rem 1.5rem;
              border: none;
              border-radius: 25px;
              font-weight: 600;
              cursor: pointer;
              transition: all 0.3s ease;
            }
            .close-btn {
              background: rgba(255, 255, 255, 0.1);
              color: #ffe0e0;
            }
            .learn-more-btn {
              background: linear-gradient(135deg, #ff0a54, #d11046);
              color: white;
            }
            .close-btn:hover, .learn-more-btn:hover {
              transform: translateY(-2px);
            }
            @media (max-width: 768px) {
              .feature-grid {
                grid-template-columns: 1fr;
              }
            }
          `;
          document.head.appendChild(style);
        }
      }
    });
  } else {
    // Fallback if Fancybox is not available
    alert('🚀 Welcome to BlogNimeHack! Explore our amazing features including anime stickers, anonymous profiles, color-coded categories, and fun error pages!');
  }
}
