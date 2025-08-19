document.addEventListener('DOMContentLoaded', () => {
    
    /**
     * Main initialization function.
     */
    function init() {
        initializeArchCalc(document.getElementById('arch-calc-widget'));
        initializeHvacCalc(document.getElementById('hvac-calc-widget'));
        initializeDuctulator(document.getElementById('duct-calc-widget'));
        initializeClockCalc(document.getElementById('clock-calc-widget'));
        initializeVoltageDropCalc(document.getElementById('voltage-drop-widget'));
    }

    /**
     * Initializes the Architectural Calculator.
     */
    function initializeArchCalc(container) {
        if (!container) return;
        const input1 = container.querySelector('#arch-input1');
        const input2 = container.querySelector('#arch-input2');
        const operationButtons = container.querySelectorAll('.arch-op-button');
        const errorMessage = container.querySelector('#arch-error-message');
        const result1Label = container.querySelector('#arch-result1-label');
        const result1Display = container.querySelector('#arch-result1-display');
        const result2Container = container.querySelector('#arch-result2-container');
        const result2Label = container.querySelector('#arch-result2-label');
        const result2Display = container.querySelector('#arch-result2-display');
        let currentOperation = 'add';
        const gcd = (a, b) => (b === 0 ? a : gcd(b, a % b));
        const parseDimension = (str) => {
            if (!str || typeof str !== 'string' || str.trim() === '') return 0;
            let totalInches = 0;
            const input = str.trim().replace(/"/g, '');
            if (!input.includes("'") && !input.split(/[\s-]+/).some(p => !p.includes('/') && !isNaN(parseFloat(p)))) {
                const inchComponents = input.split(/[\s-]+/).filter(Boolean);
                let inches = 0;
                for (const comp of inchComponents) {
                    if (comp.includes('/')) {
                        const fracParts = comp.split('/');
                        const num = parseFloat(fracParts[0]);
                        const den = parseFloat(fracParts[1]);
                        if (isNaN(num) || isNaN(den) || den === 0) return NaN;
                        inches += num / den;
                    }
                }
                return inches;
            }
            let feet = 0;
            let inchesPart = input;
            if (input.includes("'")) {
                const parts = input.split("'");
                feet = parseFloat(parts[0]);
                if (isNaN(feet)) return NaN;
                totalInches += feet * 12;
                inchesPart = parts[1] || '';
            }
            inchesPart = inchesPart.trim();
            if (!inchesPart) return totalInches;
            const inchComponents = inchesPart.split(/[\s-]+/).filter(Boolean);
            let inches = 0;
            for (const comp of inchComponents) {
                if (comp.includes('/')) {
                    const fracParts = comp.split('/');
                    const num = parseFloat(fracParts[0]);
                    const den = parseFloat(fracParts[1]);
                    if (isNaN(num) || isNaN(den) || den === 0) return NaN;
                    inches += num / den;
                } else {
                    const num = parseFloat(comp);
                    if (isNaN(num)) return NaN;
                    inches += num;
                }
            }
            return totalInches + inches;
        };
        const formatToArchitectural = (totalInches) => {
            const isNegative = totalInches < 0;
            if(isNegative) totalInches = -totalInches;
            if (isNaN(totalInches)) return "Invalid Input";
            if (totalInches === 0) return "0\"";
            const epsilon = 1e-9;
            totalInches += epsilon;
            const denominator = 16;
            let feet = Math.floor(totalInches / 12);
            let remainingInches = totalInches % 12;
            let wholeInches = Math.floor(remainingInches);
            const fractionalPart = remainingInches - wholeInches;
            let fractionStr = '';
            if (fractionalPart * denominator >= 1) {
                let numerator = Math.round(fractionalPart * denominator);
                if (numerator === denominator) {
                    wholeInches++;
                    numerator = 0;
                }
                if (numerator > 0) {
                    const commonDivisor = gcd(numerator, denominator);
                    fractionStr = `${numerator / commonDivisor}/${denominator / commonDivisor}`;
                }
            }
            if (wholeInches === 12) {
                feet++;
                wholeInches = 0;
            }
            const feetStr = feet > 0 ? `${feet}'` : '';
            const inchStr = wholeInches > 0 ? `${wholeInches}` : (feet > 0 && fractionStr ? '0' : '');
            let parts = [];
            if (feetStr) parts.push(feetStr);
            let inchPart = '';
            if(inchStr && fractionStr) {
                inchPart = `${inchStr}-${fractionStr}"`;
            } else if (inchStr) {
                inchPart = `${inchStr}"`;
            } else if (fractionStr) {
                inchPart = `${fractionStr}"`;
            }
            if(inchPart) parts.push(inchPart);
            if (parts.length === 0) return "0\"";
            return (isNegative ? '-' : '') + parts.join(' ');
        };
        function calculate() {
            const val1 = input1.value;
            const val2 = input2.value;

            if (!val1 && !val2) {
                result1Display.textContent = '...';
                result2Display.textContent = '...';
                errorMessage.classList.add('hidden');
                return;
            }

            const inches1 = parseDimension(val1);
            const inches2 = parseDimension(val2);

            if (isNaN(inches1) || isNaN(inches2)) {
                errorMessage.textContent = "Invalid format. Use formats like 12' 3-1/4\"";
                errorMessage.classList.remove('hidden');
                result1Display.textContent = '...';
                result2Display.textContent = '...';
                return;
            }
            errorMessage.classList.add('hidden');
            let res1 = '', res2 = '';
            result1Label.parentElement.classList.remove('hidden');
            result2Container.classList.remove('hidden');
            switch (currentOperation) {
                case 'add':
                case 'subtract':
                    const totalInches = currentOperation === 'add' ? inches1 + inches2 : inches1 - inches2;
                    res1 = formatToArchitectural(totalInches);
                    res2 = `${(totalInches / 12).toFixed(4)} ft`;
                    result1Label.textContent = 'Architectural';
                    result2Label.textContent = 'Decimal Feet';
                    break;
                case 'multiply':
                    const sqInches = inches1 * inches2;
                    const sqFeet = sqInches / 144;
                    res1 = `${sqFeet.toFixed(4)} sq ft`;
                    res2 = `${sqInches.toFixed(2)} sq in`;
                    result1Label.textContent = 'Area (sq ft)';
                    result2Label.textContent = 'Area (sq in)';
                    break;
                case 'divide':
                    if (inches2 === 0) {
                        errorMessage.textContent = "Cannot divide by zero.";
                        errorMessage.classList.remove('hidden');
                        res1 = 'Error';
                    } else {
                        const ratio = inches1 / inches2;
                        res1 = `${ratio.toFixed(4)}`;
                    }
                    result1Label.textContent = 'Ratio';
                    result2Container.classList.add('hidden');
                    break;
            }
            result1Display.textContent = res1;
            result2Display.textContent = res2;
        }
        input1.addEventListener('input', calculate);
        input2.addEventListener('input', calculate);
        operationButtons.forEach(button => {
            button.addEventListener('click', () => {
                currentOperation = button.dataset.op;
                operationButtons.forEach(btn => btn.classList.remove('arch-op-active'));
                button.classList.add('arch-op-active');
                calculate();
            });
        });
        container.querySelector('button[data-op="add"]').classList.add('arch-op-active');
        calculate();
    }
	
	/**
	 * Initializes the HVAC Conversion Calculator.
	 */
	function initializeHvacCalc(container) {
		if (!container) return;
		const conversionTypeSelect = container.querySelector('#hvac-conversion-type');
		const equipmentContainer = container.querySelector('#hvac-equipment-type-container');
		const equipmentTypeSelect = container.querySelector('#hvac-equipment-type');
		const title = container.querySelector('#hvac-title');
		const topInput = container.querySelector('#hvac-input-top');
		const topLabel = container.querySelector('#hvac-label-top');
		const bottomOutput = container.querySelector('#hvac-output-bottom');
		const bottomLabel = container.querySelector('#hvac-label-bottom');
		const swapBtn = container.querySelector('#hvac-swap-btn');
		
		// Conversion constants from MINHERS chart
		const CONVERSION_FACTORS = {
			btu_kw: 3412.14,
			seer_seer2: {
				ductless: 1.00,
				ducted_split: 0.95,
				ducted_packaged: 0.95
			},
			hspf_hspf2: {
				ductless: 0.90,
				ducted_split: 0.85,
				ducted_packaged: 0.84
			}
		};

		let modeStates = {
			btu_kw: { isForward: true }, // true: Btu/h -> kW
			seer_seer2: { isForward: false }, // false: SEER2 -> SEER (Default)
			hspf_hspf2: { isForward: false }  // false: HSPF2 -> HSPF (Default)
		};

		function updateCalculator() {
			const conversionType = conversionTypeSelect.value;
			const isForward = modeStates[conversionType].isForward;
			const equipmentType = equipmentTypeSelect.value;
			
			let titleText, topLabelText, bottomLabelText, topPlaceholder, factor;

			// Show/hide equipment type dropdown
			if (conversionType === 'seer_seer2' || conversionType === 'hspf_hspf2') {
				equipmentContainer.classList.remove('hidden');
			} else {
				equipmentContainer.classList.add('hidden');
			}

			switch(conversionType) {
				case 'btu_kw':
					factor = CONVERSION_FACTORS.btu_kw;
					if (isForward) {
						titleText = 'Btu/h to Kilowatts (kW)';
						topLabelText = 'Btu/h'; bottomLabelText = 'Kilowatts (kW)';
						topPlaceholder = 'Enter value in Btu/h';
					} else {
						titleText = 'Kilowatts (kW) to Btu/h';
						topLabelText = 'Kilowatts (kW)'; bottomLabelText = 'Btu/h';
						topPlaceholder = 'Enter value in kW';
					}
					break;
				case 'seer_seer2':
					factor = CONVERSION_FACTORS.seer_seer2[equipmentType];
					 if (isForward) {
						titleText = 'SEER to SEER2';
						topLabelText = 'SEER'; bottomLabelText = 'SEER2';
						topPlaceholder = 'Enter SEER value';
					} else {
						titleText = 'SEER2 to SEER';
						topLabelText = 'SEER2'; bottomLabelText = 'SEER';
						topPlaceholder = 'Enter SEER2 value';
					}
					break;
				case 'hspf_hspf2':
					factor = CONVERSION_FACTORS.hspf_hspf2[equipmentType];
					 if (isForward) {
						titleText = 'HSPF to HSPF2';
						topLabelText = 'HSPF'; bottomLabelText = 'HSPF2';
						topPlaceholder = 'Enter HSPF value';
					} else {
						titleText = 'HSPF2 to HSPF';
						topLabelText = 'HSPF2'; bottomLabelText = 'HSPF';
						topPlaceholder = 'Enter HSPF2 value';
					}
					break;
			}

			title.textContent = titleText;
			topLabel.textContent = topLabelText;
			topInput.placeholder = topPlaceholder;
			bottomLabel.textContent = bottomLabelText;
			
			const sourceValue = parseFloat(topInput.value);
			let result = '';
			if (!isNaN(sourceValue) && topInput.value.trim() !== '') {
				if (conversionType === 'btu_kw') {
					 result = isForward ? (sourceValue / factor).toFixed(4) : (sourceValue * factor).toFixed(2);
				} else {
					 result = isForward ? (sourceValue * factor).toFixed(2) : (sourceValue / factor).toFixed(2);
				}
			}
			bottomOutput.value = result;
		}

		swapBtn.addEventListener('click', () => {
			const conversionType = conversionTypeSelect.value;
			modeStates[conversionType].isForward = !modeStates[conversionType].isForward;
			topInput.value = bottomOutput.value;
			updateCalculator();
		});

		[conversionTypeSelect, equipmentTypeSelect].forEach(el => {
			el.addEventListener('change', () => {
				topInput.value = '';
				updateCalculator();
			});
		});

		topInput.addEventListener('input', updateCalculator);

		updateCalculator(); 
	}

    /**
     * Initializes the Ductulator Calculator.
     */
    function initializeDuctulator(container) {
        if (!container) return;
        const airflowCFMInput = container.querySelector('#duct-airflowCFM');
        const sizingMethodRadios = container.querySelectorAll('input[name="duct-sizingMethod"]');
        const velocityInputContainer = container.querySelector('#duct-velocityInputContainer');
        const velocityFPMInput = container.querySelector('#duct-velocityFPM');
        const frictionLossInputContainer = container.querySelector('#duct-frictionLossInputContainer');
        const frictionLossWGInput = container.querySelector('#duct-frictionLossWG');
        const ductShapeRadios = container.querySelectorAll('input[name="duct-ductShape"]');
        const aspectRatioContainer = container.querySelector('#duct-aspectRatioContainer');
        const aspectRatioInput = container.querySelector('#duct-aspectRatio');
        const calculateBtn = container.querySelector('#duct-calculateBtn');
        const roundResultDiv = container.querySelector('#duct-roundResult');
        const rectangularResultDiv = container.querySelector('#duct-rectangularResult');
        const flexResultDiv = container.querySelector('#duct-flexResult');
        const roundDiameterSpan = container.querySelector('#duct-roundDiameter');
        const rectWidthSpan = container.querySelector('#duct-rectWidth');
        const rectHeightSpan = container.querySelector('#duct-rectHeight');
        const flexDiameterSpan = container.querySelector('#duct-flexDiameter');
        const areaResultDiv = container.querySelector('#duct-areaResult');
        const calculatedAreaSpan = container.querySelector('#duct-calculatedArea');
        const messageBox = container.querySelector('#duct-messageBox');
        const messageText = container.querySelector('#duct-messageText');
        const FLEX_DUCT_CORRECTION_FACTOR = 1.25;

        function showMessage(message) {
            messageText.textContent = message;
            messageBox.classList.remove('hidden');
        }
        function hideMessage() {
            messageBox.classList.add('hidden');
            messageText.textContent = '';
        }
        function hideAllResults() {
            roundResultDiv.classList.add('hidden');
            rectangularResultDiv.classList.add('hidden');
            flexResultDiv.classList.add('hidden');
            areaResultDiv.classList.add('hidden');
        }

        sizingMethodRadios.forEach(radio => {
            radio.addEventListener('change', () => {
                if (radio.value === 'velocity') {
                    velocityInputContainer.classList.remove('hidden');
                    frictionLossInputContainer.classList.add('hidden');
                } else {
                    velocityInputContainer.classList.add('hidden');
                    frictionLossInputContainer.classList.remove('hidden');
                }
                hideAllResults();
                hideMessage();
            });
        });

        ductShapeRadios.forEach(radio => {
            radio.addEventListener('change', () => {
                if (radio.value === 'rectangular') {
                    aspectRatioContainer.classList.remove('hidden');
                } else {
                    aspectRatioContainer.classList.add('hidden');
                }
                hideAllResults();
                hideMessage();
            });
        });

        calculateBtn.addEventListener('click', () => {
            hideAllResults();
            hideMessage();
            const airflowCFM = parseFloat(airflowCFMInput.value);
            const selectedSizingMethod = container.querySelector('input[name="duct-sizingMethod"]:checked').value;
            const selectedShape = container.querySelector('input[name="duct-ductShape"]:checked').value;
            const aspectRatio = parseFloat(aspectRatioInput.value);
            let areaSqIn, diameterEquivalent;

            if (isNaN(airflowCFM) || airflowCFM <= 0) {
                showMessage('Please enter a valid positive number for Airflow (CFM).');
                return;
            }

            if (selectedSizingMethod === 'velocity') {
                const velocityFPM = parseFloat(velocityFPMInput.value);
                if (isNaN(velocityFPM) || velocityFPM <= 0) {
                    showMessage('Please enter a valid positive number for Velocity (FPM).');
                    return;
                }
                areaSqIn = (airflowCFM / velocityFPM) * 144;
                diameterEquivalent = 2 * Math.sqrt(areaSqIn / Math.PI);
            } else {
                const frictionLossWG = parseFloat(frictionLossWGInput.value);
                if (isNaN(frictionLossWG) || frictionLossWG <= 0) {
                    showMessage('Please enter a valid positive number for Friction Loss (in. wg / 100 ft).');
                    return;
                }
                diameterEquivalent = Math.pow((0.109136 * Math.pow(airflowCFM, 1.9)) / frictionLossWG, 1 / 5.02);
                areaSqIn = Math.PI * Math.pow(diameterEquivalent / 2, 2);
            }

            if (selectedShape === 'rectangular' && (isNaN(aspectRatio) || aspectRatio <= 0)) {
                showMessage('Please enter a valid positive number for Aspect Ratio.');
                return;
            }

            calculatedAreaSpan.textContent = areaSqIn.toFixed(2);
            areaResultDiv.classList.remove('hidden');

            if (selectedShape === 'round') {
                roundDiameterSpan.textContent = diameterEquivalent.toFixed(2);
                roundResultDiv.classList.remove('hidden');
            } else if (selectedShape === 'rectangular') {
                const height = Math.sqrt(areaSqIn / aspectRatio);
                const width = aspectRatio * height;
                rectWidthSpan.textContent = width.toFixed(2);
                rectHeightSpan.textContent = height.toFixed(2);
                rectangularResultDiv.classList.remove('hidden');
            } else if (selectedShape === 'flex') {
                const flexDiameter = diameterEquivalent * FLEX_DUCT_CORRECTION_FACTOR;
                flexDiameterSpan.textContent = flexDiameter.toFixed(2);
                flexResultDiv.classList.remove('hidden');
            }
        });
        
        // Initial state
        container.querySelector('input[name="duct-sizingMethod"][value="frictionLoss"]').checked = true;
        velocityInputContainer.classList.add('hidden');
        frictionLossInputContainer.classList.remove('hidden');
        if (container.querySelector('input[name="duct-ductShape"]:checked').value !== 'rectangular') {
            aspectRatioContainer.classList.add('hidden');
        }
    }
    
    /**
     * Initializes the Clock Calculator.
     */
    function initializeClockCalc(container) {
        if (!container) return;
        const startTimeInput = container.querySelector('#clock-startTime');
        const endTimeInput = container.querySelector('#clock-endTime');
        const calculateBtn = container.querySelector('#clock-calculateBtn');
        const resultContainer = container.querySelector('#clock-result-container');
        const resultDisplay = container.querySelector('#clock-result');
        const messageBox = container.querySelector('#clock-messageBox');

        function calculateTimeDifference() {
            const startTime = startTimeInput.value;
            const endTime = endTimeInput.value;

            if (!startTime || !endTime) {
                resultContainer.classList.add('hidden');
                messageBox.classList.remove('hidden');
                return;
            }
            
            messageBox.classList.add('hidden');
            const startDate = new Date(`1970-01-01T${startTime}:00`);
            const endDate = new Date(`1970-01-01T${endTime}:00`);
            let diffInMillis = endDate.getTime() - startDate.getTime();

            if (diffInMillis < 0) {
                diffInMillis += 24 * 60 * 60 * 1000;
            }

            const diffInHours = diffInMillis / 3600000;
            resultDisplay.textContent = diffInHours.toFixed(2);
            resultContainer.classList.remove('hidden');
        }
        calculateBtn.addEventListener('click', calculateTimeDifference);
    }
    
    /**
     * Initializes the Voltage Drop Calculator.
     */
    function initializeVoltageDropCalc(container) {
        if (!container) return;
        const startVoltageInput = container.querySelector('#voltage-start');
        const currentInput = container.querySelector('#voltage-current');
        const awgSelect = container.querySelector('#voltage-awg');
        const distanceInput = container.querySelector('#voltage-distance');
        const dropVSpan = container.querySelector('#voltage-drop-v');
        const dropPctSpan = container.querySelector('#voltage-drop-pct');
        const endVoltageSpan = container.querySelector('#voltage-end');

        // K value for copper wire (resistivity)
        const K_COPPER = 12.9;

        function calculateVoltageDrop() {
            const startVoltage = parseFloat(startVoltageInput.value);
            const current = parseFloat(currentInput.value);
            const cma = parseFloat(awgSelect.value); // Circular Mil Area from select value
            const distance = parseFloat(distanceInput.value);

            if ([startVoltage, current, cma, distance].some(isNaN)) {
                dropVSpan.textContent = '...';
                dropPctSpan.textContent = '...';
                endVoltageSpan.textContent = '...';
                return;
            }

            // Voltage Drop Formula: VD = 2 * K * I * L / CMA
            // We use 2 * L because distance is one-way, but current flows both ways.
            const voltageDrop = (2 * K_COPPER * current * distance) / cma;
            const endVoltage = startVoltage - voltageDrop;
            const dropPercentage = (voltageDrop / startVoltage) * 100;

            dropVSpan.textContent = voltageDrop.toFixed(2);
            dropPctSpan.textContent = dropPercentage.toFixed(2);
            endVoltageSpan.textContent = endVoltage.toFixed(2);
        }

        [startVoltageInput, currentInput, awgSelect, distanceInput].forEach(el => {
            el.addEventListener('input', calculateVoltageDrop);
        });

        // Initial calculation on load
        calculateVoltageDrop();
    }

    // Initialize all calculators on the page
    init();
});
