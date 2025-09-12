# Knowledge Base Search Instructions

## Overview
This knowledge base contains podcast episodes, webinars, and blog posts. To search efficiently, follow this hierarchical approach rather than reading all files.

## Step 1: Check the Index Files First
Always start with the index files to understand content structure and find relevant entries:

- **`podcast_index.md`** - Contains all podcast episodes with summaries, tags, and timecodes
- **`webinar_index.md`** - Contains webinar content with summaries and tags  
- **`blogs_index.md`** - Contains blog posts with summaries and tags
- **`tags_master.yaml`** - Master list of all available tags

## Step 2: Use Targeted Search Strategies

### Option A: Tag-Based Search (Most Efficient)
1. Check `tags_master.yaml` for relevant tags
2. **If you don't find relevant tags, ask for more instructions** - the knowledge base may not contain content on your topic, or you may need to search with different keywords
3. Use `grep` to search for specific tags across index files:
   ```bash
   grep -i "your-tag" podcast_index.md webinar_index.md blogs_index.md
   ```
4. This will show you exactly which content contains your topic

### Option B: Content Search
1. Use `grep` to search for keywords across the entire knowledge base:
   ```bash
   grep -i "your-keyword" /path/to/knowledge-base
   ```
2. This will show you all files containing your keyword with line numbers

### Option C: Semantic Search
1. Use codebase search tools with natural language queries
2. Ask questions like "How does X work?" or "What is Y?"
3. This finds conceptually related content even if exact keywords don't match

## Step 3: Read Only Relevant Files
Based on search results, read only the specific files that contain your topic:

- **Podcast content**: `/the-good-thing/ep[XX]/ep[XX]-[YY]-[description].md`
- **Webinar content**: `/webinar/[date]/[date]-[XX]-[description].md`  
- **Blog content**: `/blogs/[date]-[description].md`

## Step 4: Use File Structure to Your Advantage
- Each content type has a consistent naming pattern
- Index files contain summaries, so you can often get the gist without reading full files
- Tags are standardized across all content types

## Example: Searching for "MCP"
1. Check `tags_master.yaml` → find "mcp" tag
2. Search indexes: `grep -i "mcp" podcast_index.md webinar_index.md blogs_index.md`
3. Found 887 matches across knowledge base
4. Read only the most relevant files:
   - `/the-good-thing/ep09/ep09-14-introduction-to-mcp.md`
   - `/the-good-thing/ep14/ep14-05-mcp-gateway-and-json-schema.md`
   - `/webinar/2025-08-25cosmoConnect/2025-08-25-12-qa-mcp-vision.md`

## Best Practices
- **Never read all files** - use search to identify relevant content first
- **Start with indexes** - they contain summaries and metadata
- **Use tags** - they're standardized and comprehensive
- **Ask for help if no relevant tags found** - the knowledge base may not contain your topic
- **Be specific** - targeted searches are faster than broad ones
- **Read selectively** - only read files that contain your topic

## Tools Available
- `grep` - for exact text searches
- `codebase_search` - for semantic/conceptual searches  
- `read_file` - for reading specific files
- Index files - for content discovery and metadata

This approach allows you to find comprehensive information on any topic without reading hundreds of files.
