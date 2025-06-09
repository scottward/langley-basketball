## **Langley Men's Pick-Up Basketball**

![Basketball Court](court-from-top.jpg)

## **Next Run**

<span id="next-session" style="background: yellow; padding: 6px; display: inline; font-size: 21px;">Tuesday or Thursday this week</span>
<p>
 <a href="#interested">Click here to get on the list.</a>
</p>

<script>
function updateNextSessionDate() {
    // Check for test datetime in URL params
    const urlParams = new URLSearchParams(window.location.search);
    const testDatetime = urlParams.get('testDatetime');
    
    let pstTime;
    if (testDatetime) {
        // Parse test datetime using ISO 8601 format (2025-06-10T06:30 or 2025-06-10T06:30:00)
        const decoded = decodeURIComponent(testDatetime);
        
        // Parse as ISO string - JavaScript's Date constructor handles this natively
        pstTime = new Date(decoded);
        
        // Verify it parsed correctly
        if (isNaN(pstTime.getTime())) {
            console.error(`Invalid test datetime format: ${decoded}. Use ISO format like 2025-06-10T06:30`);
            // Fall back to current time
            const now = new Date();
            const pstOffset = -8;
            pstTime = new Date(now.getTime() + (pstOffset * 60 * 60 * 1000));
        } else {
            console.log(`Using test datetime: ${pstTime.toLocaleString()}`);
        }
    } else {
        // Get current date and time in PST
        const now = new Date();
        const pstOffset = -8; // PST is UTC-8
        pstTime = new Date(now.getTime() + (pstOffset * 60 * 60 * 1000));
    }
    
    const currentDay = pstTime.getDay(); // 0 = Sunday, 1 = Monday, ..., 6 = Saturday
    const currentHour = pstTime.getHours();
    const currentMinute = pstTime.getMinutes();
    
    // Check if current time is after 6:30 AM (630 minutes from midnight)
    const isAfter630AM = (currentHour > 6) || (currentHour === 6 && currentMinute >= 30);
    
    let nextSessionDate = new Date(pstTime);
    let targetDay;
    
    // If it's Tuesday or Thursday after 6:30 AM, we need the "other" day
    if ((currentDay === 2 || currentDay === 4) && isAfter630AM) {
        // Switch to the other day: Tuesday (2) -> Thursday (4), Thursday (4) -> Tuesday (2)
        targetDay = currentDay === 2 ? 4 : 2;
        const daysToAdd = currentDay === 2 ? 2 : 5; // Tue->Thu: +2, Thu->Tue: +5
        nextSessionDate.setDate(nextSessionDate.getDate() + daysToAdd);
    } else {
        // Find the next Tuesday or Thursday (including today if before 6:30 AM)
        const daysUntilTuesday = (2 - currentDay + 7) % 7;
        const daysUntilThursday = (4 - currentDay + 7) % 7;
        
        if (daysUntilTuesday <= daysUntilThursday) {
            nextSessionDate.setDate(nextSessionDate.getDate() + daysUntilTuesday);
            targetDay = 2;
        } else {
            nextSessionDate.setDate(nextSessionDate.getDate() + daysUntilThursday);
            targetDay = 4;
        }
    }
    
    // Set time to 6:30 AM
    nextSessionDate.setHours(6, 30, 0, 0);
    
    // Format the date using built-in JS formatting
    const formatter = new Intl.DateTimeFormat('en-US', {
        weekday: 'long',
        month: 'long', 
        day: 'numeric',
        hour: 'numeric',
        minute: '2-digit',
        hour12: true
    });
    
    const formattedDate = formatter.format(nextSessionDate)
        .replace(/(\d+)/, '$1' + getOrdinalSuffix(nextSessionDate.getDate()))
        .replace(/AM|PM/, match => match.toLowerCase());
    
    // Helper for ordinal suffix
    function getOrdinalSuffix(num) {
        const lastDigit = num % 10;
        const lastTwoDigits = num % 100;
        
        if (lastTwoDigits >= 11 && lastTwoDigits <= 13) return 'th';
        
        switch (lastDigit) {
            case 1: return 'st';
            case 2: return 'nd';
            case 3: return 'rd';
            default: return 'th';
        }
    }
    
    // Update the span element
    const element = document.getElementById('next-session');
    if (element) {
        element.textContent = formattedDate;
    }
    
    return formattedDate;
 }
 
 // Call the function to update the date
 updateNextSessionDate();
</script>

## **Overview**

* Fun, friendly, competitive play.
* Open to players throughout the Fraser Valley.
* Tuesdays and Thursday mornings at 6:30am.

**Experience playing basketball is necessary.**

## **Location**

![Town and Field Church](town-and-field-church.png)

Games graciously hosted by [Town and Field Church](https://townandfield.ca/) located at [20719 48 Avenue, Langley, BC, V3A 3L7](https://goo.gl/maps/283R8xNWTGZxmEnH8).

The program is organized by [Holy Nativity Orthodox Church](https://www.holynativitychurch.ca/).


## **Time**

* Every **Tuesday** and **Thursday** morning
* 6:30am - 8am
* We'll text the day before to confirm that there are enough players


## **Cost**

* Entry is by donation as you are able. Everyone is welcome regardless of your ability to donate a specific amount.
* Suggested donation amount is $5 per session.
* We don't collect any money.
* Participants donate directly to one of Town and Field's local ministry partners:
  *  [Nightshift](https://nightshiftministries.org/donate/)
  *  [Hope for Women](https://www.hopeforwomen.ca/?form=FUNUCMFYHQY)
  *  [Burnaby Counselling Group](https://counsellinggroup.org/donate/)
* Consider giving over above the suggested amounts if you are able since these are good causes and it is a way of thanking Town and Field for their hospitality. Also it covers the giving for players who aren’t able to donate the suggested amount.

**IMPORTANT:** Donations are on the honour system! You are responsible to donate in accordance with how often you play ball.

<h2 id="interested"><strong>Interested?</strong></h2>

* Text/call Scott at 604.700.4426 to get on the interested player list.
* When we text for confirmation, respond with whether you plan to come the following day.
* Play ball!


<p><br></p>
<p><br></p>
   
![Hoop From Below](hoop-from-below.jpg)


