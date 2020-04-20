# JavaScript--Largest-Sum-Non-Adjacent
Daily coding problem number 9
#__________________________________________#



const largestSumNonAdjacentNumbers = (nums) => {
  
  let prevInclusive = 0;
  let prevExclusive = 0;
  
  //i: 0 1 2 3 4 5
  //  [4,1,1,4,2,1]
  // i = 0; prevInclusive: 4; prevExclusive: 0;
  // i = 1; prevInclusive: Max(prevExclusive + 1, prevInclusive) = 4; prevExclusive = 4; 
  // i = 2; prevInclusive: Max(4 + 1, prevInclusive) = 5;  prevExclusive = 4;
  // i = 3; prevInclusive: Max(4 + 4, 5) = 8; prevExclusive = 5;
  // i = 4; prevInclusive: Max(5 + 2, 8) = 8; prevExclusive = 8;
  // i = 5; prevInclusive: Max(8 + 1, 8) = 9; prevExclusive = 8;
  
  for(let i = 0; i < nums.length; i++) {
    const current = nums[i];
    const temp = prevInclusive;
	
    prevInclusive = Math.max((prevExclusive + current), prevInclusive);
    prevExclusive= temp;
  }
  
  return Math.max(prevExclusive, prevInclusive);
 
};

const areEqual = (a, b, desc) => {
  if(a !== b) {
    console.log(`${desc} ... FAIL: ${a} !== ${b}`);
  } else {
    console.log(`${desc} ... PASS`);
  }
}


let desc = 'more complicated case';
let input =  [4,1,1,4,2,1];
let output = largestSumNonAdjacentNumbers(input);

let expected = 9;

areEqual(output, expected, desc);

-----------------------------------------------
Test that you can validate with:
console.log(largestSumNonAdjacentNumbers([5,4,3,2,5]));   //returns 13
console.log(largestSumNonAdjacentNumbers([5,1,1,5]));    //returns 10
console.log(largestSumNonAdjacentNumbers([2,4,6,2,5])); //returns 13
