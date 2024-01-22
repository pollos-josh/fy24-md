[[Bootcamp Notes]]
---

# Getting Started
Remember to include the jQuery library

```html
<script type = "text/javascript" src = "jquery-latest.js"></script>
```
# Ready Events
```javascript
$(document).ready(function() {
	// code
});
```

```javascript
$(document).ready(function() {
	var islandsContainer = $('#islandsContainer);

	islandData.forEach(function (island)) {
		islandsContainer.append(createIslandCard(island));
	}
})
```

```
            <p><strong>Region:</strong> Atlantic Ocean</p>
            <p><strong>Location:</strong> Azores, Portugal</p>
            <p><strong>Development:</strong> Adventure Hub</p>
            <p><strong>Title:</strong> Azorean Expeditions</p>
            <p><strong>Type:</strong> Adventure Tourism Island</p>
            <p><strong>Size:</strong> 60 acres</p>
            <p><strong>Lifestyles:</strong> Hiking, Whale Watching, Eco-Tourism</p>

            <p>Find peace and serenity in a cove where turquoise waters meet lush greenery and gentle sea breezes.</p>
            <p>Price: $850.00</p>
            <div class="tags">
                <span class="tag">Peaceful Retreat</span>
                <span class="tag">Nature Exploration</span>
                <span class="tag">Bird Watching</span>
            </div>
```