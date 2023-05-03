Download Link: https://assignmentchef.com/product/solved-cs302-project-4-path-finding
<br>
<strong>                                                                                                                                                                                                                                                                                                                                    </strong><strong>Project 04: Path Finding</strong>




<strong>Overview</strong>

<strong>The fourth project is to implement a path finding component of a game, either online (web application) or on your computer. You are allowed to work with a single partner (group of 2) but this will not required.</strong>

<strong>Big picture</strong>

<strong>Consider the following text and graphical representation of a 2D landscape:</strong>

<table>

 <tbody>

  <tr>

   <td width="276"><strong>Text</strong></td>

   <td width="103"><strong>Tiles</strong></td>

   <td width="539"><strong>Map</strong></td>

   <td width="0"></td>

  </tr>

  <tr>

   <td rowspan="3" width="276"><strong>hfmrhghfmr </strong><strong>mg hmhhGgGm </strong><strong>mrgfmG rmrG </strong><strong>ff rGGghmf r </strong><strong>g rh rhGmfGh </strong><strong>mGGG r rg rfG </strong><strong>mg rmgGmhgf </strong><strong>G rf rmhmmmm </strong><strong>rmfGGgfgGh </strong><strong>hhh rmffmhm</strong></td>

   <td width="103"></td>

   <td rowspan="2" width="539"></td>

   <td width="0"></td>

  </tr>

  <tr>

   <td rowspan="2" width="103"><strong>f(3) </strong><strong>g(1) </strong><strong>G(2) </strong><strong>h(4) </strong><strong>m(7) </strong><strong>r(5)</strong></td>

  </tr>

  <tr>

   <td width="539">I I                                                                          II milk                                                                   11<sub>s</sub>t“greMlkII</td>

   <td width="0"></td>

  </tr>

 </tbody>

</table>




<strong>Each tile has a symbol (e.g., a forest has “f”, river has “r”) and can be assigned a specific cost, i.e., forest has a cost of 3 and river has a cost of 5. Your mission, which you must choose to accept, is to help the runner (orange guy above) go from cell (x,y) to cell (i, j) with the lowest overall cost.</strong>




<strong>                                                                                                                                                                                                                                                                                                                                  </strong><strong>Project 04: Path Finding</strong>

<strong>Dijkstras</strong>

<strong>For this project, you will need to implement Dijkstra’s Algorithm (</strong><a href="https://en.wikipedia.org/wiki/Dijkstra%2527s_algorithm)"><strong>https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm)</strong></a><strong> in the </strong><strong>src/dijkstras.cpp </strong><strong>file.</strong>

<strong>The </strong><strong>dijkstras </strong><strong>path finding component will be given the specification of the tile information, the map layout, the runner’s location, and the target location </strong><strong>via standard input (</strong><a href="https://en.wikipedia.org/wiki/Standard_streams#Standard_input_.28stdin.29)"><strong>https://en.wikipedia.org/wiki/Standard_streams#Standard_input_.28stdin.29)</strong></a><strong> in the following format:</strong>

<strong>TILES_N</strong>

<strong>TILE_NAME_O TILE_COST_O</strong>

<ul>

 <li><strong> •</strong></li>

</ul>

<strong>TILE_NAME_N -1 TI LE_COST_N -1</strong>

<strong>MAP_ROWS MAP_COLUMNS </strong><strong>TILE_EL0         . . .</strong>

<ul>

 <li><strong> •</strong></li>

</ul>

<strong>RUNNER_START_ROW RUNNER_START_COL </strong><strong>RUNNER_END_ROW RUNNER_END_COL</strong>

<strong>The first </strong><strong>TILES_N </strong><strong>indicates the number of different tiles. This is followed by the specified number tiles, where each line has the tile name and then its </strong><strong>corresponding cost.</strong>

<strong>Next, the number of rows and columns in the map is given in </strong><strong>MAP_ROWS </strong><strong>and </strong><strong>MAP_COLUMNS . </strong><strong>This is followed by all the tile symbols where each row is </strong><strong>separated by a newline and each column is separated by a space.</strong>

<strong>Finally, you are given the runner’s starting and ending map coordinates.</strong>

<strong>Here is an example of this input:</strong>




<strong>                                                                                                                                                                                                                                                                                                                                      </strong><strong>Project 04: Path Finding</strong>

<strong>6</strong>

<ul>

 <li><strong>3</strong></li>

</ul>

<strong>g 1</strong>

<ul>

 <li><strong>2</strong></li>

</ul>

<strong>h 4</strong>

<strong>m 7</strong>

<ul>

 <li><strong>5</strong></li>

</ul>

<strong>10 10</strong>

<ul>

 <li><strong>rggmmmrfm</strong></li>

 <li><strong>grGGGGmf h </strong><strong>mrfmmfGrhh</strong></li>

 <li><strong>mGfhrgmgg </strong><strong>gggmhmhfmf </strong><strong>hrgfffghrh </strong><strong>mGf rmmGrgf </strong><strong>mrhhhhGmmr</strong></li>

 <li><strong>rgfGrrmf r</strong></li>

 <li><strong>grggrhmmr</strong></li>

 <li><strong>0</strong></li>

</ul>

<strong>7 6</strong>

<strong>Once this information is read in and parsed, the </strong><strong>dijkstras </strong><strong>application should perform Dijkstra’s Algorithm (</strong><a href="https://en.wikipedia.org/wiki/Dijkstra%2527s_algorithm)"><strong>https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm)</strong></a><strong> to determine the shortest path from the runner’s starting location to the target ending position. The </strong><strong>result of this computation should be printed to standard output (</strong><a href="https://en.wikipedia.org/wiki/Standard_streams#Standard_output_.28stdout.29)"><strong>https://en.wikipedia.org/wiki/Standard_streams#Standard_output_.28stdout.29)</strong></a><strong> in the </strong><strong>following format:</strong>

<strong>Cost</strong>

<strong>ROW_0 COL _0</strong>

<ul>

 <li>• •</li>

</ul>

<strong>That is, the first item to be printed is the total path cost, followed by the tiles to travel starting from the runner’s starting position to the target destination. </strong><strong>Here is the output your program should emit given the example input above:</strong>




<strong>                                                                                                                                                                                                                                                                                                                              </strong><strong>Project 04: Path Finding</strong>

<strong>27</strong>

<strong>0 0</strong>

<ul>

 <li><strong>1</strong></li>

 <li><strong>2</strong></li>

 <li><strong>3 1 3 1 4 1 5</strong></li>

</ul>

<strong>1 6</strong>

<strong>2 6</strong>

<strong>3 6</strong>

<strong>4 6</strong>

<strong>5 6</strong>

<strong>6 6</strong>

<strong>7 6</strong>

<strong>To test your program, you can use </strong>make test , <strong>which will run </strong>dijkstras <strong>against 4 different maps.</strong>

<strong>Note, as we will discuss in class, and similar to SuperBall — there may be multiple valid shortest paths if different paths have the same total weight. </strong><strong>Because of this, if the tests fail, let us know and we will verify if it is a false negative or not.</strong>

<strong>Calculating Path Cost</strong>

<strong>To calculate the total cost of the path and to determine the tiles to travel, you will need to reconstruct the path backwards as discussed in class. In </strong><strong>computing the total cost, remember to only include the cost of leaving a tile. This means, we should include the cost of leaving the starting tile but not out of the destination (because we never leave it).</strong>

<strong>Additional questions</strong>

<strong>When you are finished implementing your </strong>dijkstras <strong>implementation answer the following questions in your </strong><strong>README . md :</strong>

<ol>

 <li><strong> Write a program, </strong>generate_map , <strong>that given </strong><strong>N </strong><strong>generates a </strong><strong>NxN </strong><strong>map of random tiles. Use this program to generate random maps with the </strong><strong>following values of </strong><strong>N :</strong></li>

</ol>

10, 20, 50, 100, 200, 500, 1000

<strong>Benchmark your </strong>dijkstras <strong>path finding component on each of these map sizes and record the elapsed time and memory usage in a Markdown </strong><strong>(</strong><a href="https://github.comiadam-p/markdown-here/wiki/Markdown-Cheatsheet)"><strong>https://github.comiadam-p/markdown-here/wiki/Markdown-Cheatsheet)</strong></a><strong> table as demonstrated below:</strong>




<strong>                                                                                                                                                                                                                                                                                                                                      </strong><strong>Project 04: Path Finding</strong>

<table>

 <tbody>

  <tr>

   <td width="187"><strong>N</strong></td>

   <td colspan="2" width="114"><strong>Elapsed Time</strong></td>

   <td colspan="2" width="661"><strong>Memory Usage</strong></td>

  </tr>

  <tr>

   <td width="187"><strong>10</strong></td>

   <td width="25">· •</td>

   <td width="89">•</td>

   <td width="25">·    •</td>

   <td width="636">•</td>

  </tr>

  <tr>

   <td width="187"><strong>20</strong></td>

   <td width="25">· •</td>

   <td width="89">•</td>

   <td width="25">·    •</td>

   <td width="636">•</td>

  </tr>

  <tr>

   <td width="187"><strong>50</strong></td>

   <td width="25">·    •</td>

   <td width="89">•</td>

   <td width="25">·    •</td>

   <td width="636">•</td>

  </tr>

  <tr>

   <td width="187"><strong>100</strong></td>

   <td width="25">·    •</td>

   <td width="89">•</td>

   <td width="25">·    •</td>

   <td width="636">•</td>

  </tr>

  <tr>

   <td width="187"><strong>200</strong></td>

   <td width="25">·    •</td>

   <td width="89">•</td>

   <td width="25">·    •</td>

   <td width="636">•</td>

  </tr>

  <tr>

   <td width="187"><strong>500</strong></td>

   <td width="25">·    •</td>

   <td width="89">•</td>

   <td width="25">·    •</td>

   <td width="636">•</td>

  </tr>

  <tr>

   <td width="187"><strong>1000</strong></td>

   <td width="25">·    •</td>

   <td width="89">•</td>

   <td width="25">·    •</td>

   <td width="636">•</td>

  </tr>

 </tbody>

</table>




<strong>Note: You should run multiple trials (e.g </strong><strong>5 ) </strong><strong>and average the results.</strong>

<strong>Note: You should choose the top-left and bottom-right corners as the starting and ending points respectively.</strong>

<strong>In addition to the table above, each member must provide a brief summary of their individual contributions to the project and each member must </strong><strong>independently answer the following questions based on the shared table above:</strong>

<ol>

 <li><strong>How did you represent the map as a graph?</strong></li>

</ol>

<strong>Explain which graph representation you used and how you determined the relationship between vertices include the edges and their weights.</strong>

<ol start="2">

 <li><strong>What is complexity of your implementation of Dijkstra’s Algorithm (</strong><a href="https://en.wikipedia.org/wiki/Dijkstra%2527s_algorithm)?"><strong>https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm)?</strong></a> <strong>Explain this by describing which data structures you used and how you used them to implement path finding.</strong></li>

 <li><strong>How well does your implementation scale?</strong></li>

</ol>

<strong>Explain what effect did </strong><strong>N </strong><strong>(ie. the size of the map) have on the performance of your </strong><strong>dijkstras </strong><strong>path finding component in terms of execution time </strong><strong>and memory usage?</strong>

<strong>Submission instructions</strong>

<strong>Please have one team member submit an archive of the following files (not in a subdirectory of the archive) on Canvas to aid us in grading:</strong>

<ol>

 <li><strong>source files for dijkstras</strong></li>

 <li><strong>source files for generate_map</strong></li>

 <li><a href="http://README.md"><strong>md</strong></a><strong> with required table</strong></li>

 <li><strong>Text document summarizing the student who is uploading’s contributions and their answers to the required questions</strong></li>

 <li><strong>Makefile (even if you use the provided Makefile, please include it) that does the following:</strong></li>

</ol>

<strong>o compiles your code into an executable called “dijkstras”</strong>

<strong>                                                                                                                                                                                                                                                                                                                                   </strong><strong>Project 04: Path Finding</strong>

<strong>o </strong><strong>creates an executable called generate_map from your generate_map code (either by compiling it if you write in a compiled language or by </strong><strong>running chmod to make it executable </strong>if <strong>you didn’t write in a compiled language)</strong>

<strong>If you work in a pair, the team member who isn’t submitting the above files should write up a separate document with their contributions/answers (see </strong><strong>above) and submit only that on Canvas.</strong>

<strong>Rubric</strong>

<strong>Your project will be scored as follows:</strong>

<strong>+2   Code is well formatted, commented (inc. name, assignment, and overview), with reasonable variable names</strong>

<strong>+5  Passes memory tests</strong>

<strong>+20  Test cases successfully solved (5 points each)</strong>

<strong>+10 Generate_map works properly</strong>

<strong>+8   Table and responses, inc. individual contributions</strong>

<strong>We reserve the right to take off up to three points for submissions that do not follow the new requested format designed to streamline TA grading effort for the initial pass.</strong>