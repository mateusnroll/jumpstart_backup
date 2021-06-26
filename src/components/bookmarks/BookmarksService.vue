<script>
import ChromeBookmarks from './ChromeBookmarksService.vue'

/**
 * Service to work with the browser's bookmarks
 */
export default {
	// Gets all the bookmarks
	// @arg noOrphans Boolean - If true will return only folders on the first
	//                          level, wrapping orphans in an untitled folder
	// @arg rootId String - The id of the node that will be considered the root
	all(rootId = null, noOrphans = true) {
		return new Promise(resolve => {
			ChromeBookmarks.all(rootId).then(bookmarks => {
				if (noOrphans) bookmarks = this.cleanupOrphans(bookmarks)
				resolve(bookmarks)
			})
		})
	},

	// Cleans up any first-level items that are not folders. Any
	// orphans are added to a group with no title, and it is appended
	// to the end of the bookmark array.
	// @arg bookmarks Array - The array of bookmarks to be cleaned up
	cleanupOrphans(bookmarks) {
		var filtered = bookmarks.filter(b => b.type == 'folder')
		var orphans = bookmarks.filter(b => b.type == 'bookmark')

		filtered.push({ title: '(orphans)', type: 'folder', children: orphans})
		return filtered
	}
}
</script>