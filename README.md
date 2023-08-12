<h1>OrderflowChart</h1><p>Welcome to the <b>OrderflowChart</b> repository! This project empowers you to visualize orderflow footprint charts effortlessly using Python and Plotly.</p><h2>Usage</h2><p>The heart of the project is the <code>OrderFlowChart</code> class constructor. It's designed to simplify the process of plotting orderflow data on footprint charts, leveraging Plotly's capabilities.</p><h3>Constructor</h3><pre><div class="bg-black rounded-md mb-4"><div class="flex items-center relative text-gray-200 bg-gray-800 px-4 py-2 text-xs font-sans justify-between rounded-t-md"></div><div class="p-4 overflow-y-auto"><code class="!whitespace-pre hljs language-python"><span class="hljs-keyword">from</span> OrderFlow <span class="hljs-keyword">import</span> OrderFlowChart

<span class="hljs-comment"># Read orderflow data from CSV</span>
orderflow_data = pd.read_csv(
    ORDERFLOW_CSV,
    names=[<span class="hljs-string">'bid_size'</span>, <span class="hljs-string">'price'</span>, <span class="hljs-string">'ask_size'</span>, <span class="hljs-string">'identifier'</span>],
    index_col=<span class="hljs-number">0</span>,
    parse_dates=<span class="hljs-literal">True</span>
)

<span class="hljs-comment"># Read OHLC data from CSV</span>
ohlc_data = pd.read_csv(
    OHLC_CSV,
    index_col=<span class="hljs-number">0</span>,
    parse_dates=<span class="hljs-literal">True</span>,
    names=[<span class="hljs-string">'open'</span>, <span class="hljs-string">'high'</span>, <span class="hljs-string">'low'</span>, <span class="hljs-string">'close'</span>, <span class="hljs-string">'identifier'</span>]
)

<span class="hljs-comment"># Create an instance of OrderFlowChart</span>
orderflowchart = OrderFlowChart(
    orderflow_data,
    ohlc_data,
    identifier_col=<span class="hljs-string">'identifier'</span>
)

<span class="hljs-comment"># Plot the orderflow chart</span>
orderflowchart.plot()
</code></div></div></pre>
<h3>Parameters</h3>
<ul>
<li><p>
<code>orderflow_data</code>: Your orderflow data, containing columns like 'bid_size', 'price', 'ask_size', and 'identifier'. If the 'imbalance' column needs to be calculated, simply provide it along with the previous mentioned columns</p></li>
<li><p>
<code>ohlc_data</code>: Your OHLC data with columns 'open', 'high', 'low', 'close', and 'identifier'. The 'identifier' column bridges the gap between orderflow and OHLC data.</p></li>
<li><p>
<code>identifier_col</code>: The column that uniquely identifies candles in both datasets. Incase your data is time-indexed i.e. each candle has a unique timestamp that acts as index, pass <i>None</i>.</p></li>
<li><p>
<code>imbalance_col</code>: The column name that contains imbalance for each price level. Provide None if to be calculated.</p></li>
</ul><h3>Output</h3><p>The above code snippet generates a stunning orderflow chart like this:</p><p><img src="image.png" alt="OrderFlowChart Example"></p><p>With OrderflowChart, you can effortlessly transform complex orderflow data into visually appealing and insightful footprint charts. Feel free to explore, customize, and gain new perspectives from your data with this powerful tool.</p>
