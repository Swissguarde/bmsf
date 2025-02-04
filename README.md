STEP 1: First, in the handleSubmit function, after calculating the moments, you call calculateBMSF:

function calculateBMSF(spans, moments) {
for each span: 1. Calculate start and end reactions using: - Span length - Load type (UDL, point load, etc.) - Load magnitude - Start and end moments

    2. For UDL:
       - Shear Force = Reaction - (w * x)
       - Bending Moment = (Reaction * x) - (w * x²/2) + start moment

    3. For Point Load:
       - Shear Force changes at point load location
       - Bending Moment has different equations before and after load point

    4. Store critical points:
       - Start and end points
       - Points where load is applied
       - Points where shear force becomes zero

}

STEP 2: The extractCriticalBMSF function identifies important points along each span where:

- The shear force is zero (maximum/minimum bending moment)
- Point loads are applied
- Support locations
- Any other significant changes in the beam's behavior

For example ,
// For a UDL span:

const shearForce = (x: number) => {
return startReaction - (loadMagnitude \* x);
}

const bendingMoment = (x: number) => {
return (startReaction _ x) - (loadMagnitude _ x \* x / 2) + startMoment;
}

// For a point load span:
const shearForce = (x: number) => {
if (x < pointLoadDistance) {
return startReaction;
} else {
return startReaction - pointLoadMagnitude;
}
}

const bendingMoment = (x: number) => {
if (x < pointLoadDistance) {
return (startReaction _ x) + startMoment;
} else {
return (startReaction _ x) - pointLoadMagnitude \* (x - pointLoadDistance) + startMoment;
}
}

The results are then used to plot the shear force and bending moment diagrams
